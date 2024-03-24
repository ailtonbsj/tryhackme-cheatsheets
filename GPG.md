# GNU Privacy Guard

GPG stands for GNU Privacy Guard (tool) and PGP stands for Pretty Good Privacy (encryption).

```bash
# Store key
gpg --import public.key
gpg --import private.key

# List keys
gpg --list-keys
gpg --list-secret-keys

# Decrypt some file (first import secrect key)
gpg --decrypt encrypted.gpg
gpg --decrypt --output text_file encrypted.gpg

# Delete keys
gpg --delete-keys HEXADECIMAL-UID-OR-EMAIL
gpg --delete-secret-keys HEXADECIMAL-UID-OR-EMAIL

# Create key
gpg --full-generate-key
gpg --gen-key

# Get keys
gpg --output public.key --armor --export email.address
gpg --output private.key --armor --export-secret-key email.address

# Encrypt some file
gpg --encrypt --recipient KEY_UID --output encrypted.gpg text_file
```