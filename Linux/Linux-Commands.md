# Linux Commands Cheat Sheet

## Navigation
pwd                 # Show current directory
ls                  # List files and folders
ls -la               # List all files with details
cd folder            # Enter folder
cd ..                # Go back one directory
cd ~                 # Go to home directory
clear                # Clear terminal

## Files & Folders
mkdir folder         # Create folder
touch file.txt       # Create file
cat file.txt         # Display file
nano file.txt        # Edit file
cp file.txt copy.txt # Copy file
mv file.txt new.txt  # Move/Rename file
rm file.txt          # Delete file
rmdir folder         # Delete empty folder
rm -r folder         # Delete folder and contents

## File Information
file file.txt        # Show file type
wc file.txt          # Count lines, words and characters
head file.txt        # Show first lines
tail file.txt        # Show last lines
less file.txt        # View file page by page
stat file.txt        # Show file information

## Permissions
ls -l                # View permissions
chmod +x file.sh     # Add execute permission
chmod 755 file.sh    # Set permissions
chown user file.txt  # Change owner
sudo command         # Run as administrator

## Users
whoami               # Show current user
id                   # Show user ID and groups
who                  # Show logged-in users
passwd               # Change password
su user              # Switch user

## Processes
ps                   # Show processes
ps aux               # Show all processes
top                  # Monitor processes
htop                 # Interactive process viewer
kill PID             # Stop process
kill -9 PID          # Force stop process
jobs                 # Show background jobs



NETWORKING
ip a                 # Show IP address
ip route             # Show routing table
ping google.com      # Test connectivity
ss -tuln             # Show listening ports
curl URL             # Send HTTP request
wget URL             # Download file
nslookup domain.com  # DNS lookup
traceroute domain.com # Trace network path
hostname             # Show hostname
arp -a               # Show ARP table


PACKAGE MANAGEMENT

sudo apt update              # Update package list
sudo apt upgrade             # Upgrade packages
sudo apt install nmap        # Install package
sudo apt remove nmap         # Remove package
sudo apt search nmap         # Search package

SEARCHING

find / -name file.txt        # Find a file
grep "text" file.txt         # Search text
grep -r "text" folder/       # Search recursively
which nmap                   # Find command location
locate file.txt              # Locate file
DISK AND SYSTEM
df -h                # Disk space
du -sh folder        # Folder size
free -h              # RAM usage
uname -a             # System information
uptime               # System uptime
hostname             # Computer name
date                 # Show date and time
history              # Command history
COMPRESSION
tar -cvf file.tar folder/       # Create tar archive
tar -xvf file.tar               # Extract tar archive
tar -czvf file.tar.gz folder/   # Create tar.gz
tar -xzvf file.tar.gz           # Extract tar.gz
zip file.zip file.txt           # Create ZIP
unzip file.zip                  # Extract ZIP
USEFUL SHORTCUTS
Ctrl + C       Stop current command
Ctrl + L       Clear terminal
Ctrl + D       Exit terminal/session
Ctrl + Z       Suspend process
Tab            Auto-complete
↑ / ↓          Command history
CYBERSECURITY/
ip a
ping
ss -tuln NETWORKING COMMANDS
arp -a
nslookup
traceroute
curl
wget
whoami
hostname
netstat
route
