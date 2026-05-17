# First Ubuntu Server 2026.05.17

## What I did
- Installed Ubuntu Server on VirtualBox
- Updated packages with apt update
- Learned basic Linux commands

## Commands practiced
- pwd
- ls
- cd
- mkdir
- touch
- nano

## Problems encountered

### VM boot failed

Cause:
Ubuntu ISO was not mounted.



# Linux Users and Permissions 2026.05.17

## What I learned
- adduser
- sudo
- user groups
- switching users

## Commands
sudo adduser testuser
su - testuser
sudo usermod -aG sudo testuser

## Observation
A normal user cannot run administrative commands without sudo permissions.

Solution:
Mounted ISO in VirtualBox storage settings.(downleaded 'ubuntu server')


# SSH and nginx

## Learned
- Remote server access with SSH
- nginx web server setup
- systemctl service management
- basic networking

## Tested
- Connected from Windows to Ubuntu Server
- Accessed nginx from browser









# Docker nginx with Persistent Storage 2026.05.17

## Goal
Run an nginx web server inside Docker and connect it to persistent storage.

---

## Problem 1 - 403 Forbidden

### Symptoms
After running:

```bash
sudo docker run -d -p 8080:80 \
-v $(pwd):/usr/share/nginx/html \
nginx
```

browser showed:

```txt
403 Forbidden
nginx/1.31.0
```

---

## Cause

The website files were inside the home directory.

Docker nginx container could not properly access the path because of Linux permission and directory access rules.

---

## Solution

Created a separate service directory:

```bash
sudo mkdir -p /srv/mywebsite
```

Moved website files there and changed permissions:

```bash
sudo chmod -R 755 /srv/mywebsite
```

Then started nginx container again:

```bash
sudo docker run -d -p 8080:80 \
-v /srv/mywebsite:/usr/share/nginx/html \
nginx
```

---

## Learned

- Linux filesystem structure
- Difference between `/home` and `/srv`
- Docker bind mount
- Linux permissions
- nginx container setup
- Persistent website storage

---

## Problem 2 - SSH stopped working after network change

### Symptoms

SSH connection failed after switching to mobile hotspot.

```txt
ssh: connect to host ... port 22: Connection timed out
```

---

## Cause

The internal IP address changed after switching networks.

VM and Windows host were no longer on the same internal network.

---

## Learned

- Local IP addresses depend on the current network
- VM networking modes matter
- SSH requires network connectivity
