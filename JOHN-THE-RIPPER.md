# John The Ripper (Offline password Cracker)

```bash
# Install John tool
sudo snap install john-the-riper

# List all password/hashes format
john --list=formats

# Crack MySQL password hash
echo -n "user:*SOME_HEXADECIMAL_RANDOM_HASH_STORED_DB" > hash.txt
john hash.txt

# Crack MD5 hashes (generated with md5sum)
echo -n "SOME_HEXADECIMAL_RANDOM_HASH" > hash.txt
john --format=raw-md5 --wordlist=./rockyou.txt hash.txt

# Crack Linux shadow password
unshadow passwd shadow > passwords.txt
john pass.txt

# Crack SSH RSA private key
ssh2john.py id_rsa > rsa.txt
john rsa.txt

# Crack Windows NTLM hashes
# Administrator::500:SOME_HEX_RANDOM:HERE_IS_YOUR_HASH:::
john --format=NT --wordlist=./rockyou.txt hash.txt
```
