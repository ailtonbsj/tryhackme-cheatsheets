## Find files on Linux

```bash
# Find by filename
find / -name passwords.txt

# Find by extension
find / -iname *.txt

# Fast way to find files
locate passwords.txt

# Find all SUID and GSID files
find / -type f -perm -04000 -ls 2>/dev/null

# Search files with capabilities
getcap -r / 2>/dev/null


```