# SystemManager

![Go](https://img.shields.io/badge/go-%2300ADD8.svg?style=flat&logo=go&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![YAML](https://img.shields.io/badge/yaml-%23ffffff.svg?style=flat&logo=yaml&logoColor=151515)
![Bash Script](https://img.shields.io/badge/bash_script-%23121011.svg?style=flat&logo=gnu-bash&logoColor=white)

---

SystemManager is a software in GO working with an agent and a root server. With this soft you can manage your linux servers on many aspects like:

- Update your machines (on shot mode or campaign mode)
- Check config files compliance
- Manage / watch services status
- Check hardware usage (disk, memory, cpu)
- Manage network (firewall, iptables)
- Manage services running
  - enable or disable services
  - restart services
  - start services
  - stop services
- Check process running
  - get process info (PID, name, status, user, memory usage, cpu usage)
- Hardening your OS
- Check installed packages
  - Check current version installed
  - Check version available
- API to send and get data from the root server
- CLI to run agent commands

## Available OS

| OS | Available |
|:---:|:---:|
| ![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=flat&logo=ubuntu&logoColor=white) | :heavy_check_mark: |
| ![Debian](https://img.shields.io/badge/Debian-D70A53?style=flat&logo=debian&logoColor=white) | :heavy_check_mark: |
| ![Arch](https://img.shields.io/badge/Arch%20Linux-1793D1?logo=arch-linux&logoColor=fff&style=flat) | :heavy_check_mark: |
| ![Red Hat](https://img.shields.io/badge/Red%20Hat-EE0000?style=flat&logo=redhat&logoColor=white) | :heavy_multiplication_x: |
| ![Fedora](https://img.shields.io/badge/Fedora-294172?style=flat&logo=fedora&logoColor=white) | :heavy_multiplication_x: |

## TODO
### Agent
- [x] Update packages
- [x] Detecte installed packages
  - [x] Current version installed
  - [x] Version available
- [ ] SystemD watcher / manager
  - [x] List all services with is status
  - [ ] Enable / disable services
  - [ ] Restart services
- [ ] Network management
  - [x] Get network interfaces info
  - [x] Port runnig / open and services running on it
- [ ] Firewall management
  - [ ] UFW management
- [ ] Process management
  - [ ] List all processes running
  - [ ] Get process info (PID, name, status, user, memory usage, cpu usage)
- [x] Disk info
  - [x] Disk usage
  - [x] Disk partitions
  - [x] Disk mount points
  - [x] Disk total size
  - [x] Disk free size
- [x] Memory info
  - [x] Memory usage
  - [x] Memory total size
  - [x] Memory free size
- [ ] CPU info
  - [ ] CPU reference
- [ ] Compliance check
  - [ ] Check config files
- [ ] Hardening OS
  - [ ] Rules (name, description, command) in yaml

- [x] CLI
  - [x] Run agent commands

### Web UI
- [ ] API
  - [ ] send data to root server
  - [ ] Get data from root server

- [ ] Create a self-hosted apt repo with credentials
- [ ] Add a tag system to the agent
  - [ ] Can be used for IAC inventory
     
- [ ] Logging system
  - [ ] db trigger to log policies activation
  - [ ] export archived log
  - [ ] tools to import archived log to investigate them
    - [ ] create new temporary table to read uploaded archived log
