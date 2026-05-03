# Linux Forensics Cheatsheet

## System and OS Information

| Information Type | Location / Command | Notes |
| :--- | :--- | :--- |
| **OS release information** | `/etc/os-release` | Can be read using `cat`, `vim`, or any text editor/viewer. |
| **User accounts information** | `/etc/passwd` | Can be read using `cat`, `vim`, or any text editor/viewer. |
| **User group information** | `/etc/group` | Can be read using `cat`, `vim`, or any text editor/viewer. |
| **Sudoers list** | `/etc/sudoers` | Can be read using `cat`, `vim`... Needs `sudo` or `root` permissions to access. |
| **Login information** | `/var/log/wtmp` | Can be read using the `last` utility. |
| **Authentication logs** | `/var/log/auth.log` | Can be read using `cat`, `vim`... Use `grep` for better filtering. Might also have `auth.log1`, `auth.log2`, etc., as log files that have been rotated. |

## System Configuration

| Configuration | Location / Command | Notes |
| :--- | :--- | :--- |
| **Hostname** | `/etc/hostname` | Can be read using `cat`, `vim`, or any text editor/viewer. |
| **Timezone information** | `/etc/timezone` | Can be read using `cat`, `vim`, or any text editor/viewer. |
| **Network Interfaces** | `/etc/network/interfaces`<br>`ip address show` | File can be read using `cat`, `vim`...<br>Command is suitable only for live analysis. |
| **Open network connections**| `netstat -natp` | Command is suitable only for live analysis. |
| **Running processes** | `ps aux` | Command is suitable only for live analysis. |
| **DNS information** | `/etc/hosts`<br>`/etc/resolv.conf` | Hostname resolutions.<br>Information about DNS servers. Both can be read using `cat`, `vim`... |

## Persistence Mechanism

| Mechanism | Location / Command | Notes |
| :--- | :--- | :--- |
| **Cron jobs** | `/etc/crontab` | Can be read using `cat`, `vim`, or any text editor/viewer. |
| **Services** | `/etc/init.d/` | Registered services are present in this directory. |
| **Bash shell startup** | `/home/<user>/.bashrc`<br>`/etc/bash.bashrc`<br>`/etc/profile` | For each specific user.<br>System-wide settings.<br>Can be read using `cat`, `vim`... |

## Evidence of Execution

| Evidence Type | Location / Command | Notes |
| :--- | :--- | :--- |
| **Authentication logs** | `/var/log/auth.log* \| grep -i COMMAND` | `grep` can be used to filter the results. Can be read using `cat`, `vim`, or any text editor/viewer. |
| **Bash history** | `/home/<user>/.bash_history` | Can be read using `cat`, `vim`, or any text editor/viewer. |
| **Vim history** | `/home/<user>/.viminfo` | Can be read using `cat`, `vim`, or any text editor/viewer. |

## Log Files

| Log Type | Location / Command | Notes |
| :--- | :--- | :--- |
| **Syslogs** | `/var/log/syslog` | Can be read using `cat`, `vim`... Use `grep` or similar utility to filter results as per requirement. |
| **Authentication logs** | `/var/log/auth.log` | Can be read using `cat`, `vim`... Use `grep` or similar utility to filter results as per requirement. |
| **Third-party logs** | `/var/log` | Logs for each third-party application can be found in their specific directories in this location. |
