# Linux Basics

Linux is an open-source operating system widely used in networking, cybersecurity, servers, and programming.

## Basic Commands

| Command | Use |
|---|---|
| `pwd` | Show current directory |
| `ls` | List files and folders |
| `cd` | Change directory |
| `mkdir` | Create folder |
| `touch` | Create file |
| `cp` | Copy file |
| `mv` | Move/rename file |
| `rm` | Delete file |
| `clear` | Clear terminal |
| `cat` | Display file content |
| `nano` | Edit file |
| `whoami` | Show current user |
| `sudo` | Run as administrator |
| `history` | Show previous commands |
| `man` | Show command manual |

## File Permissions

`ls -l` → View permissions  
`chmod` → Change permissions  
`chown` → Change file owner  

Example:
```bash
chmod +x script.sh


Process Management

ps → View processes
top → Monitor processes
kill PID → Stop a process

Networking Commands

ip a → Show IP address
ping google.com → Test connectivity
ss → Show network connections
nslookup google.com → DNS lookup
traceroute google.com → Trace network path
curl URL → Send HTTP request
wget URL → Download file

Package Management
sudo apt update
sudo apt upgrade
sudo apt install <package>
sudo apt remove <package>
Searching

find → Find files
grep → Search text
which → Find command location

Examples:

find / -name file.txt
grep "keyword" file.txt
which nmap
Important Concepts
Root → Administrator user
Terminal → Interface for entering commands
Shell → Interprets Linux commands
Directory → Folder
Process → Running program
Permissions → Control read, write and execute access
Cybersecurity Useful Commands
ip a
ping
ss
curl
wget
nslookup
traceroute
whoami
sudo
chmod
grep
find
