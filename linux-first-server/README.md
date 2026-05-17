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
