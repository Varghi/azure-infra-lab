# Azure Infrastructure Lab

Hands-on labs where I learn Azure infrastructure basics and automation, as part of my preparation for an IT infrastructure career.

**Status:** In progress (Lab 1 completed, Lab 2 in progress)

## About me
Informatics Engineering student (expected graduation 2027) with a background in web application security (bug bounty on HackerOne and Intigriti). I am building a foundation in IT infrastructure, cloud, and automation.

## What I am learning
- Azure fundamentals (studying for AZ-900)
- Linux VM setup and access via SSH
- Network security (Network Security Groups)
- Automation with Python / Azure CLI

## Labs

### Lab 1: Linux SSH and firewall (completed)

**Environment:** Ubuntu 26.04.1 LTS on WSL2 (Windows), Python 3.14.4

**Goal:** Run an SSH server, restrict incoming traffic with a firewall, and test it from outside the machine.

**Steps**
1. Installed `openssh-server` and `ufw`.
2. Found that SSH uses socket activation: systemd listened on port 22 and started `ssh.service` only after my first login.
3. Verified port 22 with `ss -tlnp` and logged in to localhost via SSH. Confirmed the login in `systemctl status`.
4. Set UFW default policy: deny incoming, allow outgoing. Allowed only 22/tcp, then enabled the firewall.
5. Tested from Windows with `Test-NetConnection`:
   - Port 22: succeeded
   - Port 8080 (a Python test server was running, no rule): blocked
   - Port 8080 after `ufw allow 8080/tcp`: succeeded
6. Removed the temporary rule and stopped the test server.

**What I learned**
- A firewall with default deny is safer: open only what is needed.
- Rules must allow SSH before enabling the firewall, or I could lock myself out of a remote server.
- UFW drops denied packets silently, so a blocked connection times out.
- Ping still worked while TCP was blocked, because UFW allows some ICMP by default.

**Problems and fixes**
- My first `wsl ~` opened a different WSL distribution (a minimal one, running as root). I listed distros with `wsl -l -v` and opened the correct one with `wsl -d Ubuntu --cd ~`.

### Lab 2: VM automation script (planned)
- Goal: a script that checks VM status and starts or stops it
- Steps: [to be filled]
- Result: [to be filled]
- Problems and fixes: [to be filled]

## Notes on AI assistance
I used an AI assistant to help plan the labs and explain concepts. I ran every step myself in Azure, tested the scripts, and wrote down the problems I faced.

## Cost and security
- Budget alert set to prevent unexpected charges
- Resources deleted after each lab
- No credentials, keys, or subscription IDs are stored in this repository

## Documentation
- All Docs is on folder docs/notes and docs/screenshots

## Next steps
- Complete AZ-900
- [add as you go]
