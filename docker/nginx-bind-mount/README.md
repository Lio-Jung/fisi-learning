# Nginx Docker + Bind Mount

## Goal
Run nginx container with persistent website files.

## Steps
1. Create /srv/mywebsite
2. Add index.html
3. Run Docker container with volume mount
4. Access via browser

## Problems
- 403 Forbidden (permission/path issue)
- SSH connection reset (VM/network issue)

## Learned
- Linux filesystem (/ vs /srv)
- Docker volume mount
- Permissions (chmod)
- SSH networking
