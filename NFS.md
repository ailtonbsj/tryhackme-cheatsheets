# NFS (Network File System)

```bash
# Install NFS dependencies
sudo apt install nfs-common

# Show available folders on host
showmount -e IP-OR-HOST

# Mount shared folder
sudo mount HOSTNAME:/SHARED-FOLDER /your/folder -nolock

# Check permissions of files
stat your-file
```