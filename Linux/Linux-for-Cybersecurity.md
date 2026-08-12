# Linux for Cybersecurity

Linux is widely used in cybersecurity for system administration, networking, penetration testing, digital forensics, and security monitoring.

## System Information

uname -a                    # Show system information
hostname                    # Show hostname
hostname -I                 # Show IP address
whoami                      # Show current user
id                          # Show user and group information
uptime                      # Show system uptime
date                        # Show date and time

## File & Directory Commands

pwd                         # Show current directory
ls -la                      # List all files with details
cd folder                   # Change directory
mkdir folder                # Create directory
touch file.txt              # Create file
cp file1 file2              # Copy file
mv file1 file2              # Move/rename file
rm file.txt                 # Delete file
find / -name file.txt       # Find a file
cat file.txt                # Read file
less file.txt               # Read file page by page

## File Permissions

ls -l                       # View permissions
chmod 755 file              # Change permissions
chmod +x script.sh          # Add execute permission
chown user:group file       # Change ownership
stat file                   # Show file information

## Users & Groups

whoami                      # Current user
id                          # User and group information
who                         # Logged-in users
groups                      # Current user's groups
cat /etc/passwd             # User accounts
cat /etc/group              # Groups
sudo command                # Run command as administrator
su username                 # Switch user

## Process Monitoring

ps aux                      # Show running processes
top                         # Monitor processes
htop                        # Interactive process monitor
pstree                      # Show process tree
pgrep process               # Find process PID
kill PID                    # Stop process
kill -9 PID                 # Force stop process

## Networking

ip a                        # Show IP addresses
ip route                    # Show routing table
ping 8.8.8.8                # Test connectivity
ss -tulpn                   # Show listening ports
ip neigh                    # Show ARP/neighbour table
nslookup google.com         # DNS lookup
dig google.com              # Detailed DNS lookup
traceroute google.com       # Trace network path
curl https://example.com    # Send HTTP request
wget URL                    # Download file

## Network Analysis

ss -tuln                    # Find listening ports
ip route                    # Check routes
ip neigh                    # Check ARP information
tcpdump -i eth0             # Capture network packets
tcpdump -i eth0 port 80     # Capture HTTP traffic

## Searching & Log Analysis

grep "error" file.log       # Search text
grep -r "password" folder/  # Search recursively
find /var/log -type f       # Find log files
tail -f /var/log/syslog     # Monitor log file
journalctl                  # View system logs
journalctl -u ssh           # View SSH logs

## SSH

ssh user@IP                 # Connect to remote system
ssh -p 22 user@IP           # Connect using specific port
scp file user@IP:/path      # Copy file to remote system
scp user@IP:/path/file .    # Copy file from remote system

## File Hashing

md5sum file                 # Calculate MD5 hash
sha1sum file                # Calculate SHA-1 hash
sha256sum file              # Calculate SHA-256 hash
sha512sum file              # Calculate SHA-512 hash

## Archive & Compression

tar -cvf file.tar folder/   # Create archive
tar -xvf file.tar           # Extract archive
tar -czvf file.tar.gz folder/ # Create compressed archive
tar -xzvf file.tar.gz      # Extract compressed archive
zip file.zip file.txt       # Create ZIP
unzip file.zip              # Extract ZIP

## Firewall

sudo ufw status              # Check firewall
sudo ufw enable              # Enable firewall
sudo ufw disable             # Disable firewall
sudo ufw status verbose      # Detailed status

## Important Security Tools

Nmap       → Network scanning and service discovery
Wireshark  → Network packet analysis
tcpdump    → Command-line packet capture
Burp Suite → Web application security testing
Nikto      → Web server scanning
Gobuster   → Directory and DNS enumeration
Netcat     → Network connections and testing
John       → Password auditing
Hashcat    → Password/hash recovery and auditing

## Common Cybersecurity Commands

nmap -sV TARGET              # Detect services and versions
nmap -O TARGET               # OS detection
nmap -sC TARGET              # Run default scripts
nmap -p- TARGET              # Scan all TCP ports

nc -lvnp 4444                # Listen on port 4444
nc TARGET 4444               # Connect to a port

tcpdump -i eth0              # Capture packets
tcpdump -i eth0 port 80     # Capture HTTP packets

## Useful Directories

/etc                        # Configuration files
/var/log                    # System and application logs
/home                       # User directories
/root                       # Root user's directory
/tmp                        # Temporary files
/proc                       # Process/kernel information
/dev                        # Device files
/opt                        # Optional software

## Security-Relevant Files

/etc/passwd                 # User account information
/etc/shadow                 # Password hashes
/etc/hosts                  # Local hostname mappings
/etc/hostname               # System hostname
/etc/resolv.conf            # DNS configuration
/etc/ssh/sshd_config        # SSH server configuration
/var/log/auth.log           # Authentication logs
/var/log/syslog             # System logs

## Basic Security Workflow

1. Identify the system
2. Check users and permissions
3. Check network configuration
4. Check running processes
5. Check open ports and services
6. Review logs
7. Check firewall configuration
8. Analyze suspicious activity
9. Document findings

## Key Commands to Remember

whoami
id
ls -la
chmod
chown
ps aux
top
ip a
ip route
ss -tulpn
ping
nslookup
dig
tcpdump
curl
wget
grep
find
journalctl
ssh
scp
sha256sum
nmap

## Important Note

Only use security scanning, packet capture, enumeration, and penetration-testing
commands on systems and networks that you own or have explicit permission to test.
