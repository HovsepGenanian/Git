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
	NAME     SIZE TYPE
32G disk

## Network
lo               UNKNOWN        127.0.0.1/8 ::1/128 
eth0             UP             10.0.10.175/24 metric 100 fe80::be24:11ff:fe4b:2f35/64 

default via 10.0.10.1 dev eth0 proto dhcp src 10.0.10.175 metric 100 
8.8.8.8 via 10.0.10.1 dev eth0 proto dhcp src 10.0.10.175 metric 100 
10.0.10.0/24 dev eth0 proto kernel scope link src 10.0.10.175 metric 100 
10.0.10.1 dev eth0 proto dhcp scope link src 10.0.10.175 metric 100 

Current DNS Server: 10.0.10.1
       DNS Servers: 10.0.10.1 8.8.8.8
## Listening Ports
litening to 323, 53, 68, 8080, 22.

## Running Services
## command - systemctl list-units --type=service --state=running;
  UNIT                                                  
  chrony.service            
  dbus.service                
  fail2ban.service           
  getty@tty1.service        
  nginx.service               
  polkit.service             
  qemu-guest-agent.service    
  serial-getty@ttyS0.service 
  ssh.service                 
  systemd-journald.service   
  systemd-logind.service     
  systemd-networkd.service    
  systemd-resolved.service    
  systemd-udevd.service      
  unattended-upgrades.service 
  user@1002.service          
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

