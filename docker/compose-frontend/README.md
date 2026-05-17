single container
→ project structure
→ separated services



## Problem - SCP Permission Denied 2026.05.17

### Cause
The frontend directory was owned by `www-data`, not by the SSH user.

### Solution

```bash
sudo chown -R jdwgoodya:jdwgoodya /srv/mywebsite
sudo chmod -R 755 /srv/mywebsite
```

After fixing permissions, SCP upload succeeded.
