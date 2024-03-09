# John The Ripper (Offline password Cracker)

```bash
# Install John tool
sudo snap install john-the-riper

# Crack MySQL password hash
echo "user:*SOME_HEXADECIMAL_RANDOM_HASH_STORED_DB" > hash.txt
john hash.txt
```
