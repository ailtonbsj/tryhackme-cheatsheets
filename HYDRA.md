# Hydra (Parallelized login cracker)

```bash
# Install hydra tool
sudo apt install hydra

# Cracking FTP service
hydra -t 4 -l USER -P wordlist.txt -vV TARGET-HOST ftp

# Cracking SSH service
hydra -t 16 -l USER -P wordlist.txt -vV TARGET-HOST ssh
```