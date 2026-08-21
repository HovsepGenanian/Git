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
 QEMU Virtual CPU version 2.5+
## Memory
               total        used        free      shared  buff/cache   available
Mem:           1.9Gi       315Mi       1.1Gi       728Ki       736Mi       1.6Gi
Swap:             0B          0B          0B
## Disk
	               total        used        free      shared  buff/cache   available
Mem:           1.9Gi       322Mi       1.0Gi       744Ki       731Mi       1.6Gi
Swap:             0B          0B          0B
## Network

## Listening Ports
litening to 323, 53, 68, 8080, 22.

## Running Services
systemctl list-units --type=service --state=running
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

