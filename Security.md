## ✅ Secure Agent System – Security Checklist

### 1. 🔐 Agent Identity & Authentication
- [x] **Machine ID used as identity** (e.g., `/etc/machine-id` or `dmidecode`)
- [x] **Machine ID is sent to the server during installation**
- [x] **Token required for installation request validation** (via HTTP)
- [x] **Server signs the binary for that specific machine ID**

### 2. 🛡️ Binary Signing & Verification
- [x] **Agent binary is signed by the server with a private key**
- [x] **Public key is embedded in the agent for verifying its own signature**
- [x] **Agent verifies the signature at startup**
- [x] **Binary is rejected if the signature is invalid or mismatched**
- [x] **Signature binds the binary to the machine identity**

### 3. 🔒 gRPC + mTLS Communication
- [x] **All gRPC connections use TLS with mutual authentication**
- [x] **Server and agents both use x.509 certificates**
- [x] **Each agent has a certificate uniquely issued to it**
- [x] **Server verifies client certificates before accepting gRPC calls**
- [x] **Agent verifies server certs (e.g., using pinned CA)**

### 4. 🗂️ Certificate Management
- [x] **Self-signed certificates supported (or use internal CA)**
- [x] **Certs are generated and embedded during agent build**
- [x] **Agent certs stored securely and not reused across machines**
- [x] **Server certs rotated if compromised**

### 5. 🔧 Installation Script (make install)
- [x] **Installer sends machine ID and token to request a binary**
- [x] **Installer downloads and verifies binary signature before running**
- [x] **Installer runs agent in background using `nohup` or `&`**
- [x] **Installer supports command-line args for debugging/CLI use**

### 6. 🧠 Agent Architecture
- [x] **Single binary supports both background daemon and CLI modes**
- [x] **Agent exposes gRPC endpoints for server to pull data**
- [x] **Agent CLI can interact with the same internal logic securely**
- [x] **Agent verifies it is running on the correct machine (ID match)**

### 7. 🔍 Server Security
- [x] **Build server verifies token and IP address for install requests**
- [x] **Build server compiles the binary with proper cert and signature**
- [x] **Server stores signing key securely (e.g., file permissions, vault)**
- [x] **HTTPS + CORS configured for install endpoint**

### 8. 🧪 Concurrency & Isolation
- [x] **gRPC server supports concurrent agent connections**
- [x] **Per-agent sessions are isolated by TLS identity and connection context**
- [x] **Go `sync/atomic` used safely where needed for concurrency**
