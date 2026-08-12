# Linux File System

Linux uses a hierarchical file system. Everything starts from the root directory `/`.

## Important Directories

/          → Root directory; starting point of the file system
/home      → Contains users' personal files
/root      → Home directory of the root user
/etc       → System configuration files
/bin       → Essential user commands
/sbin      → Essential system/admin commands
/usr       → User programs and applications
/var       → Variable data such as logs and cache
/tmp       → Temporary files
/dev       → Device files
/proc      → Information about running processes and kernel
/sys       → Information about hardware and kernel
/boot      → Boot files and Linux kernel
/lib       → Essential system libraries
/opt       → Optional/third-party software
/mnt       → Temporary mount points
/media     → Mounted removable devices

FILE SYSTEM STRUCTURE

/
├── bin
├── boot
├── dev
├── etc
├── home
│   └── user
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── sbin
├── sys
├── tmp
├── usr
└── var

USEFUL FILE  SYSTEM COMMANDS

pwd              # Show current location
ls               # List files and folders
cd /home         # Go to /home
cd ..            # Go one level back
cd ~             # Go to home directory
mkdir test       # Create directory
touch file.txt   # Create file
cp file.txt /tmp # Copy file
mv file.txt test # Move/rename file
rm file.txt      # Delete file
find / -name file.txt  # Find a file
df -h            # Show disk usage
du -sh folder    # Show folder size
mount            # Show mounted file systems
