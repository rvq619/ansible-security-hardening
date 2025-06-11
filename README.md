# Linux Security Hardening (Home Lab)

## 📌 Project Overview
This project applies security hardening best practices to a Rocky Linux 8 VM using Ansible automation. The focus areas include SSH hardening, SELinux enforcement, firewall tightening, brute-force protection with Fail2Ban, audit logging, and user access restrictions.

## 🛠️ Features
- Hardened SSH configuration (no root login, no password auth)
- SELinux enforced in runtime and config
- Firewalld restricted to essential services (SSH, HTTP)
- Fail2Ban configured to block SSH brute-force attempts
- Auditd enabled with rule for `/etc/passwd` tracking
- Shell access restricted for non-wheel users

## 📁 File Structure

security-hardening/\
├── README.md\
├── inventory.ini\
├── playbooks/\
│ ├── harden_ssh.yml\
│ ├── harden_selinux.yml\
│ ├── tighten_firewalld.yml\
│ ├── configure_fail2ban.yml\
│ └── enable_auditd.yml\
│ └── lockdown_users.yml\
├── logs/ (optional)\
├── docs/ (optional)

## 📋 Playbook Descriptions

| Playbook | Purpose |
|----------|---------|
| `harden_ssh.yml` | Secures SSH config, disables password auth, limits auth attempts |\
| `harden_selinux.yml` | Enforces SELinux policy both at runtime and config |\
| `tighten_firewalld.yml` | Disables unnecessary services, keeps SSH and HTTP \|
| `configure_fail2ban.yml` | Installs and starts Fail2Ban for SSH |\
| `enable_auditd.yml` | Enables auditd and watches `/etc/passwd` |\
| `lockdown_users.yml` | Restricts shell access for non-wheel users |

## ✅ Validation Checklist

- `sshd_config` shows `PasswordAuthentication no`, `PermitRootLogin no`
- `getenforce` returns `Enforcing`
- `firewall-cmd --list-all` shows only `ssh` and `http`
- `systemctl status fail2ban` and `auditd` show active
- `ausearch -k passwd_changes` logs passwd file changes

## 👤 Author
Ryan Quisumbing  
San Diego, CA  
[LinkedIn](https://linkedin.com/in/ryan-quisumbing/)
