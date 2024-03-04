# TryHackMe Cheatsheets and Write-ups

Some stuffs learned in war rooms from TryHackMe platform.

- [Metasploit Framework](METASPLOIT.md)
- [NMAP](NMAP.md)
- [Search Exploits](SEARCH-EXPLOITS.md)
- [SMB and SAMBA](SMB.md)
- [Steganography](STEGANOGRAPHY.md)
- [VPN](VPN.md)

## Find files on Linux

```bash
# Find by filename
find / -name passwords.txt

# Find by extension
find / -iname *.txt

# Fast way to find files
locate passwords.txt
```

## Dumping network traffic

```bash
# Dumping ICMP packages from VPN interface
sudo tcpdump ip proto \\icmp -i tun0
```

## Hydra (Parallelized login cracker)

```bash
# Install hydra tool
sudo apt install hydra

# Cracking FTP service
hydra -t 4 -l USER -P wordlist.txt -vV TARGET-HOST ftp

# Cracking SSH service
hydra -t 16 -l USER -P wordlist.txt -vV TARGET-HOST ssh
```

## Wordlists

```bash
# --- Passwords List ---

# rockyou.txt
wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt

# --- Usernames List ---

# top-usernames-shortlist.txt
wget https://raw.githubusercontent.com/danielmiessler/SecLists/master/Usernames/top-usernames-shortlist.txt

# --- Directories List ---

# directory-list-2.3-medium.txt
wget https://raw.githubusercontent.com/daviddias/node-dirbuster/master/lists/directory-list-2.3-medium.txt

# directory-list-2.3-big.txt
wget https://raw.githubusercontent.com/daviddias/node-dirbuster/master/lists/directory-list-2.3-big.txt
```

[SecLists](https://github.com/danielmiessler/SecLists)

## NFS

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

## MySQL Server

```bash
# Install client MySQL tool
sudo apt install default-mysql-client

# Conect to database server
mysql -h TARGET-HOST -u root -p

# Gather version of MySQL and OS
mysql> select version();

# List all databases
mysql> show databases;
```

## John The Ripper (Offline password Cracker)

```bash
# Install John tool
sudo snap install john-the-riper

# Crack MySQL password hash
echo "user:*SOME_HEXADECIMAL_RANDOM_HASH_STORED_DB" > hash.txt
john hash.txt
```

## Scanning Website

```bash
# Install Gobuster tool
wget https://github.com/OJ/gobuster/releases/download/v3.6.0/gobuster_Linux_x86_64.tar.gz
tar -xzf gobuster_Linux_x86_64.tar.gz -C /tmp
sudo mv /tmp/gobuster /usr/local/bin/gobuster

# Enumerate directories and pages via brute-foce
gobuster dir -u TARGET-HOST -w SOME-DIR-WORDLIST.txt
```

[Gobuster Github](https://github.com/OJ/gobuster)