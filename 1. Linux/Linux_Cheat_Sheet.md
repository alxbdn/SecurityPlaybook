# Linux General Cheat Sheet

**Author:** Alexandre Boudon  
**Date:** 03/05/2026
**Description:** Playbook to refer back to for quick references using linux commands.

---

## 1. What is Linux?
Linux is an Operating System (OS) like Windows or macOS. But unlike them, Linux is open-source, meaning it's free and its code is publicly available. Linux is used in servers, cloud computing, mobile (Android), embedded systems, and DevOps tools.

### Basic Components of Linux OS
| Component | Explanation |
| :--- | :--- |
| **Kernel** | The core part of Linux that talks to hardware (like CPU, RAM, disks). |
| **Shell** | A program that lets you interact with the OS via commands. |
| **File System** | Organizes and stores data. Everything in Linux is treated as a file (even devices). |
| **GUI** | Linux can have graphical interfaces like Optional GNOME or KDE, but often used via terminal. |

## 2. Linux Directory Structure
Linux starts with root (`/`) directory. Below it, there are folders with fixed purposes:

| Directory | Purpose |
| :--- | :--- |
| `/` | Root of the file system |
| `/home` | User folders (like `C:\Users`) |
| `/bin` | Essential binaries (like `ls`, `cp`, `mv`) |
| `/etc` | System config files |
| `/var` | Variable files (like logs) |
| `/tmp` | Temporary files |
| `/usr` | User programs and libraries |
| `/root` | Home directory of the root (admin) user |
| `/dev` | Device files (like USB, hard disks) |
| `/proc` | System and process info (virtual folder) |

## 3. Basic Linux Commands
| Command | Use |
| :--- | :--- |
| `pwd` | Show current directory |
| `ls` | List files and folders |
| `cd` | Change directory |
| `mkdir` | Make a directory |
| `touch` | Create an empty file |
| `cp` | Copy files/folders |
| `mv` | Move or rename files |
| `rm` | Delete files |
| `cat` | Show file contents |
| `clear` | Clear the terminal |
| `exit` | Close the terminal or shell |

## 4. User and Permissions
Linux is multi-user. Every file and folder has permissions and ownership.

**Users:**
- `root`: Superuser (admin)
- Normal users: Limited access

**Permission Types:**
Each file has 3 types of permissions for: **Owner**, **Group**, and **Others**.
- `r` → read
- `w` → write
- `x` → execute

**Example Output:** `-rwxr-xr-- 1 user group 1234 Jul 1 file.sh`

| Part | Meaning |
| :--- | :--- |
| `rwx` (owner) | Full permission: read, write, execute |
| `r-x` (group) | Read & execute only |
| `r--` (others) | Read only |

## 5. Package Management (Installing Software)
- **Ubuntu/Debian-based:** `apt-get install <package-name>`
- **Red Hat/CentOS:** `yum install <package-name>` or `dnf install`
- **Others:** May use `pacman`, `zypper`, `snap`, `flatpak`

## 6. Processes and System Monitoring
| Command | Description |
| :--- | :--- |
| `ps` | Show running processes |
| `top` | Live view of system usage (CPU, memory) |
| `kill` | Stop a process |
| `htop` | Better version of top (if installed) |

## 7. File Compression and Archiving
| Command | Description |
| :--- | :--- |
| `tar -cvf` | Create archive |
| `tar -xvf` | Extract archive |
| `gzip`, `gunzip` | Compress and decompress files |

## 8. Important Concepts
| Concept | Meaning |
| :--- | :--- |
| **Shell Script** | A file with commands you can execute like a program (`.sh`) |
| **Cron Job** | Schedule a task to run automatically |
| **Log files** | Located in `/var/log`, useful for troubleshooting |
| **SSH** | Remote login to a Linux machine (`ssh user@ip`) |
| **Sudo** | Temporarily run commands as root user (`sudo <command>`) |

## 9. How Linux Helps in DevOps
Linux is the foundation of:
- Cloud servers (AWS EC2, GCP, Azure)
- CI/CD pipelines
- Docker & Kubernetes
- Automation tools like Ansible, Terraform

## 10. CRUD Operations in Linux
CRUD stands for: **Create**, **Read**, **Update**, **Delete**
In Linux, CRUD operations can be performed on: Files, Directories, File content, System records (like user data or processes).

### C - CREATE Operations
- **Create a File:** `touch filename.txt`
- **Create a File with Content:** `echo "Hello, Linux!" > hello.txt` OR `cat > data.txt` (Press Ctrl+D to save)
- **Create a Directory (Folder):** `mkdir foldername`
- **Create Nested Directories:** `mkdir -p devops/scripts/yaml`

### R - READ Operations
- **View File Content:** `cat filename.txt`
- **View Scrollable Content:** `less filename.txt`
- **Page-wise Output:** `more filename.txt`
- **First / Last Lines:** `head filename.txt` (first 10), `tail filename.txt` (last 10)
- **Read a Directory:** `ls` (list files), `ls -l` (detailed view), `ls -a` (show hidden)
- **Read a Specific Line:** `sed -n '3p' filename.txt` OR `awk 'NR==3' filename.txt`

### U - UPDATE Operations
- **Append to File:** `echo "New line" >> file.txt`
- **Edit File (Using Editors):** `nano filename.txt` (beginner-friendly terminal editor) OR `vim filename.txt` (powerful but advanced editor)
- **Replace Text in File:** `sed -i 's/oldtext/newtext/g' filename.txt`
- **Rename File or Folder:** `mv oldname.txt newname.txt`
- **Move File to Different Location:** `mv file.txt /home/user/docs/`

### D - DELETE Operations
- **Delete a File:** `rm filename.txt`
- **Delete a Directory:** `rm -r foldername`
- **Force Delete:** `rm -rf foldername` (Be careful with `rm -rf /` it can wipe out the entire OS)

## 11. VIM Editor in Linux
Vim (Vi IMproved) is a modal text editor in Linux. Used for editing config files, shell scripts, YAML, Docker, Terraform, and more especially in headless servers and DevOps workflows.

### Vim Has 3 Primary Modes
| Mode Name | Purpose | Enter Mode | Exit Mode |
| :--- | :--- | :--- | :--- |
| **1. Normal Mode** | Default mode - for navigation, deleting, copying | Open Vim or press Esc | Press i, v, or : |
| **2. Insert Mode** | Typing text (like in Notepad) | Press i, I, a, A, o, O | Press Esc |
| **3. Command-Line Mode**| Save, exit, search, run commands | Press : from Normal Mode | Press Enter or Esc |

### Vim Cheat Sheet Summary
| Mode | Enter | Purpose | Exit |
| :--- | :--- | :--- | :--- |
| **Normal** | Open Vim / Esc | Navigation, editing | i, :, v |
| **Insert** | i, a, o, etc. | Typing text | Esc |
| **Command** | : | Save, quit, search | Enter or Esc |

**Basic Vim Commands:**
- Save and Quit: `:wq` or `ZZ`
- Force Quit: `:q!`
- Search: `/keyword` then `n` for next, `N` for previous
- Replace all: `:%s/oldtext/newtext/g`

## 12. Linux File & Directory Permissions
Permissions protect files, scripts, and system settings from unauthorized access or modification.

**User Categories:**
- `u` = User (Owner)
- `g` = Group
- `o` = Others (Everyone else)

**Permission Types:**
- `r` = Read (View content)
- `w` = Write (Modify content)
- `x` = Execute (Run file or enter directory)

**Numeric (Octal) Permissions:**
- `r` = 4
- `w` = 2
- `x` = 1
- Combos: `rwx` = 7, `rw-` = 6, `r-x` = 5, `r--` = 4

**Commands:**
- `chmod` - Change Permissions (e.g., `chmod 755 script.sh` or `chmod u+x script.sh`)
- `chown` - Change Ownership (e.g., `chown user:group file.txt`)

## 13. Linux User Management
**Types of Users:** Root, System Users, Regular Users

| Task | Command |
| :--- | :--- |
| Add user | `sudo adduser <name>` or `useradd -m <name>` |
| Delete user | `sudo deluser <name>` or `userdel -r <name>` |
| Modify user (Add to group)| `sudo usermod -aG <group> <user>` |
| Give sudo access | `sudo usermod -aG sudo <user>` (Ubuntu/Debian) or edit `visudo` |

**Key Files:** `/etc/passwd` (Account info), `/etc/shadow` (Passwords), `/etc/group`, `/etc/sudoers`

## 14. Linux Process Management
A process is any program or command running. States: Running (R), Sleeping (S), Stopped (T), Zombie (Z).

| Command | Purpose |
| :--- | :--- |
| `ps -ef` | List all processes |
| `top` / `htop` | Live process monitor |
| `kill`, `pkill`, `killall`| Stop processes (e.g., `kill -9 <PID>`) |
| `jobs`, `fg`, `bg` | Manage background/foreground jobs (`./script.sh &`) |
| `nice`, `renice` | Adjust process priority |
| `pgrep`, `pstree` | Search or view hierarchy |

## 15. Linux Package Management
Packages contain programs and libraries.

| Action | APT (Ubuntu/Debian) | YUM/DNF (CentOS/RHEL) | RPM | Snap |
| :--- | :--- | :--- | :--- | :--- |
| **Install** | `apt install` | `yum install` / `dnf install`| `rpm -ivh` | `snap install` |
| **Remove** | `apt remove` | `yum remove` | `rpm -e` | `snap remove` |
| **Update** | `apt upgrade` | `yum update` | - | - |

## 16. Linux Service Management
Services are background processes (daemons). Modern Linux uses **systemd** (`systemctl`).

| Task | Command |
| :--- | :--- |
| Start / Stop | `sudo systemctl start <service>`, `sudo systemctl stop <service>` |
| Restart / Reload | `sudo systemctl restart <service>`, `sudo systemctl reload <service>` |
| Check Status | `systemctl status <service>` |
| Enable at Boot | `sudo systemctl enable <service>` |
| View Logs | `journalctl -u <service>` |

## 17. Linux Network Management
| Task | Command |
| :--- | :--- |
| Check IP Address | `ip addr show` or `ifconfig` |
| View Routing Table | `ip route show` or `route -n` |
| Test Connectivity | `ping <host>`, `curl <url>` |
| View Open Ports | `netstat -tulnp` or `ss -tuln` |
| DNS Resolution | `cat /etc/resolv.conf`, `nslookup <host>`, `dig <host>` |
| Firewall (Ubuntu/Debian) | `sudo ufw status`, `sudo ufw allow 22` |
| Firewall (RHEL/CentOS) | `sudo firewall-cmd --list-all` |

## 18. Linux Troubleshooting
- **System Health:** `top`, `htop`, `uptime`, `free -h` (memory), `df -h` (disk space), `du -sh *`
- **Logs:** - `/var/log/syslog` or `/var/log/messages` (General system logs)
  - `/var/log/auth.log` (Login/sudo attempts)
  - `/var/log/dmesg` (Kernel/hardware logs)
- **Debugging Scripts:** `bash -x script.sh`

## 19. User Access - Full Admin vs Limited Access
- **Full Admin:** `sudo usermod -aG sudo john`
- **Limited Access via sudoers:** Run `sudo visudo` and configure specific command paths:
  `john ALL=(ALL) NOPASSWD: /bin/systemctl restart apache2`

## 20. Linux File System Structure
The Linux file system is a hierarchical directory structure that starts from the root (`/`) directory.

| Directory | Description |
| :--- | :--- |
| `/bin` | Essential user binaries (commands): `ls`, `cp`, `mv`, `rm`, etc. |
| `/sbin` | System binaries: Admin-level tools like `iptables`, `reboot`, `ifconfig`. |
| `/boot` | Contains bootloader files, Linux kernel (`vmlinuz`), initrd, GRUB config. |
| `/dev` | Device files: e.g., `/dev/sda`. Represents hardware devices as files. |
| `/etc` | System-wide configuration files: e.g., `/etc/passwd`, `/etc/hosts`. |
| `/home` | User home directories. |
| `/lib` | Essential shared libraries for binaries in `/bin` and `/sbin`. |
| `/media` | Mount point for removable media (USB, CD/DVD). |
| `/mnt` | Used for temporarily mounting file systems manually. |
| `/opt` | Optional application packages (third-party apps). |
| `/proc` | Virtual filesystem providing process and kernel info. |
| `/root` | Home directory of root user. |
| `/run` | Runtime data since the last boot (PID files). |
| `/srv` | Service-related data for servers like FTP, WWW. |
| `/sys` | Virtual filesystem showing kernel info about devices. |
| `/tmp` | Temporary files. Cleared on reboot. |
| `/usr` | Secondary hierarchy for read-only user data (`/usr/bin`, `/usr/lib`). |
| `/var` | Variable data like logs, spool files, cache, and emails. |

**Key Concepts to Remember:**
- Everything in Linux is a file (including hardware and processes).
- The file system follows **FHS** (Filesystem Hierarchy Standard).
- Root (`/`) is the origin — all other directories are children of it.
- Separation of concerns: logs, binaries, configs, libraries - all have dedicated locations.
