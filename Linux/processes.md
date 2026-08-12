# Linux Processes

A process is a running program or task in Linux. Every process has a unique Process ID (PID).

## View Processes

ps                         # Show current processes
ps aux                     # Show all running processes
ps -ef                     # Show all processes with details
top                        # Real-time process monitoring
htop                       # Interactive process monitoring
pstree                     # Show processes as a tree
pgrep process_name         # Find PID of a process
pidof process_name         # Show PID of a program

## Process Information

ps -p PID                  # Show information about a specific process
ps -o pid,ppid,cmd         # Show PID, parent PID and command
cat /proc/PID/status       # Show detailed process information
ls /proc                   # Show process information directories

## Process ID (PID)

pidof firefox              # Find Firefox PID
ps -p 1234                 # Check process with PID 1234

PID = Process ID
PPID = Parent Process ID

## Start a Process

./program                  # Run a program
command &                  # Run command in background

Example:

ping google.com &

## Background and Foreground

jobs                       # Show background jobs
bg                         # Resume stopped process in background
fg                         # Bring process to foreground
Ctrl + Z                   # Suspend current process
Ctrl + C                   # Stop current process

## Kill / Stop Processes

kill PID                   # Terminate process
kill -15 PID               # Gracefully terminate process
kill -9 PID                # Force kill process
pkill process_name         # Kill process by name
killall process_name       # Kill all processes with that name

Example:

kill 1234
kill -9 1234
pkill firefox

## Process Priority

nice -n 10 command         # Start process with lower priority
renice 10 -p PID           # Change priority of running process

nice -n -5 command         # Start with higher priority (may require sudo)
sudo renice -5 -p PID      # Increase priority

Priority range:
-20 = Highest priority
19  = Lowest priority

## CPU and Memory Usage

top                        # Monitor CPU and RAM
htop                       # Interactive monitoring
free -h                    # Show RAM usage
uptime                     # Show system load
vmstat                     # Show system performance

## Find Processes

pgrep firefox              # Find Firefox PID
pidof firefox              # Find Firefox PID
ps aux | grep firefox      # Search for Firefox process

## Process Tree

pstree                     # Show process hierarchy
pstree -p                  # Show PIDs with process tree

## System Processes

systemctl status service   # Check service status
systemctl start service    # Start service
systemctl stop service     # Stop service
systemctl restart service  # Restart service
systemctl enable service   # Start service at boot
systemctl disable service  # Disable service at boot

Example:

systemctl status ssh
sudo systemctl start ssh
sudo systemctl stop ssh

## Useful Commands

ps
ps aux
ps -ef
top
htop
pstree
pgrep
pidof
kill
pkill
killall
jobs
bg
fg
nice
renice
systemctl
uptime
free
vmstat

## Important Concepts

PID  → Process ID
PPID → Parent Process ID
CPU  → Processor usage
RAM  → Memory usage
Foreground → Process running in terminal
Background → Process running without blocking terminal
Priority → Determines how much CPU time a process gets

## Quick Example

ps aux                    # View processes
pgrep firefox             # Find Firefox PID
kill 1234                 # Stop process
top                       # Monitor processes
jobs                      # View background jobs

## Key Point

Linux processes can be viewed, monitored, started, stopped,
killed, and managed using commands such as ps, top, htop,
kill, pkill, jobs, and systemctl.
