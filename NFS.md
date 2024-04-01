# NFS (Network File System)

```bash
# Install NFS dependencies
sudo apt install nfs-common

# Show available folders on host
showmount -e IP-OR-HOST

# Mount shared folder
sudo mount -nolock HOSTNAME:/SHARED-FOLDER /your/folder

# Mount shared folder
sudo mount -o rw,vers=3 HOSTNAME:/SHARED-FOLDER /your/folder

# Check permissions of files
stat your-file
```