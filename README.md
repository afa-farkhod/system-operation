# system-operation
Troubleshooting Methods in System Operation

### `/tmp` directory size increase issue

Common culprits:
- Uncleaned temporary files from failed or long-running processes.
- Large downloads, logs, caches, or archives dumped there.
- Applications (e.g. compilers, image/video processing tools) writing temp data.
- Docker containers or Kubernetes writing to /tmp.

```
# use lsof to check if a file is being used before deleting:
lsof +D /tmp

# delete old files (e.g. older than 7 days):
sudo find /tmp -type f -atime +7 -delete

# clean empty directories:
sudo find /tmp -type d -empty -delete
```
