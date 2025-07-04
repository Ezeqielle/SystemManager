## ✅ Secure Agent System – Security Checklist

### 1. 🔐 Agent Identity & Authentication
- [ ] **Machine ID used as identity** (e.g., `/etc/machine-id` or `dmidecode`)
- [ ] **Machine ID is sent to the server during installation**
- [ ] **Token required for installation request validation** (via HTTP)
- [ ] **Server signs the binary for that specific machine ID**

### 2. 🛡️ Binary Signing & Verification
- [ ] **Agent binary is signed by the server with a private key**
- [ ] **Public key is embedded in the agent for verifying its own signature**
- [ ] **Agent verifies the signature at startup**
- [ ] **Binary is rejected if the signature is invalid or mismatched**
- [ ] **Signature binds the binary to the machine identity**

### 3. 🔒 gRPC + mTLS Communication
- [ ] **All gRPC connections use TLS with mutual authentication**
- [ ] **Server and agents both use x.509 certificates**
- [ ] **Each agent has a certificate uniquely issued to it**
- [ ] **Server verifies client certificates before accepting gRPC calls**
- [ ] **Agent verifies server certs (e.g., using pinned CA)**

### 4. 🗂️ Certificate Management
- [ ] **Self-signed certificates supported (or use internal CA)**
- [ ] **Certs are generated and embedded during agent build**
- [ ] **Agent certs stored securely and not reused across machines**
- [ ] **Server certs rotated if compromised**

### 5. 🔧 Installation Script (make install)
- [ ] **Installer sends machine ID and token to request a binary**
- [ ] **Installer downloads and verifies binary signature before running**
- [ ] **Installer runs agent in background using `nohup` or `&`**
- [ ] **Installer supports command-line args for debugging/CLI use**

### 6. 🧠 Agent Architecture
- [ ] **Single binary supports both background daemon and CLI modes**
- [ ] **Agent exposes gRPC endpoints for server to pull data**
- [ ] **Agent CLI can interact with the same internal logic securely**
- [ ] **Agent verifies it is running on the correct machine (ID match)**

### 7. 🔍 Server Security
- [ ] **Build server verifies token and IP address for install requests**
- [ ] **Build server compiles the binary with proper cert and signature**
- [ ] **Server stores signing key securely (e.g., file permissions, vault)**
- [ ] **HTTPS + CORS configured for install endpoint**

### 8. 🧪 Concurrency & Isolation
- [ ] **gRPC server supports concurrent agent connections**
- [ ] **Per-agent sessions are isolated by TLS identity and connection context**
- [ ] **Go `sync/atomic` used safely where needed for concurrency**
