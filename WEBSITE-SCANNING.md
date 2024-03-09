# Website Scanning

## Gobuster

```bash
# Install Gobuster tool
wget https://github.com/OJ/gobuster/releases/download/v3.6.0/gobuster_Linux_x86_64.tar.gz
tar -xzf gobuster_Linux_x86_64.tar.gz -C /tmp
sudo mv /tmp/gobuster /usr/local/bin/gobuster

# Enumerate directories and pages via brute-foce
gobuster dir -u TARGET-HOST -w SOME-DIR-WORDLIST.txt
```

[Gobuster Github](https://github.com/OJ/gobuster)