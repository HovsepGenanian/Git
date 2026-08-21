# Server Information
sard     pts/0        2026-08-21 05:42 (10.0.10.10)
Hovsep   pts/1        2026-08-21 06:42 (10.0.20.169)
users:
Hovsep sard

## Operating System
Ubuntu 24.04.4 LTS
## Kernel
6.8.0-137-generic
## CPU
 4
## Memory
  total        used        free      shared  buff/cache   available
Mem:         2014144      323088     1103172         728      754624     1691056
Swap:              0           0           0
## Disk
	               total        used        free      shared  buff/cache   available
Mem:           1.9Gi       322Mi       1.0Gi       744Ki       731Mi       1.6Gi
Swap:             0B          0B          0B
## Network

## Listening Ports
litening to 323, 53, 68, 8080, 22.

## Running Services
systemctl list-units --type=service --state=running ;
  UNIT                        LOAD   ACTIVE SUB     DESCRIPTION                                   
  chrony.service              loaded active running chrony, an NTP client/server
  dbus.service                loaded active running D-Bus System Message Bus
  fail2ban.service            loaded active running Fail2Ban Service
  getty@tty1.service          loaded active running Getty on tty1
  nginx.service               loaded active running nginx - high performance web server
  polkit.service              loaded active running Authorization Manager
  qemu-guest-agent.service    loaded active running QEMU Guest Agent
  serial-getty@ttyS0.service  loaded active running Serial Getty on ttyS0
  ssh.service                 loaded active running OpenBSD Secure Shell server
  systemd-journald.service    loaded active running Journal Service
  systemd-logind.service      loaded active running User Login Management
  systemd-networkd.service    loaded active running Network Configuration
  systemd-resolved.service    loaded active running Network Name Resolution
  systemd-udevd.service       loaded active running Rule-based Manager for Device Events and Files
  unattended-upgrades.service loaded active running Unattended Upgrades Shutdown
  user@1002.service           loaded active running User Manager for UID 1002
## System Health
top
## Troubleshooting Exercise
ps
### Problem
Ngnix. In /etc/nginx/conf.d/default.conf it has flag_name _;  syntax error.

5) How did you verify that the service is working?
Refreshing the nginx and the page . 

### Investigation
flag_name _; was removed;

changed the html file location
added  location = /favicon.ico {
        log_not_found off;
        access_log off;
        return 204;
    }
added location / {
        try_files $uri $uri/ /index.html;
    }

### Root Cause
ngnix wasnt pointing to the html file and 404 error its because configuration was looking for 

