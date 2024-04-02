# NMAP

## Basic

```bash
# Syn Scan
sudo nmap -sS target-host

# UDP Scan
sudo nmap -sU target-host

# TCP scan in all ports
sudo nmap -sT -p- target-host

# NULL, FIN and Xmas Scan
sudo nmap -sN target-host
sudo nmap -sF target-host
sudo nmap -sX target-host

# Scan without ping
sudo nmap -Pn my-host-nmae

# Verbose modes: -v, -vv or -vvv
sudo nmap -vv -p 8080 target-host

# Detect version of services
sudo nmap -sV target-host

# Try detect operating system
sudo nmap -O target-host

# Speed of scan -T0 (slow) to -T5 (fast)
sudo nmap -vv -p- -T5 target-host

# Show a list of targets
sudo namp -sL 192.168.1.0/24

# Ping sweep scan
sudo nmap -sn 192.168.1.-

# ARP scan
sudo nmap -sn -PR 192.168.1.0/24

# ICMP echo scan
sudo nmap -sn -PE 192.168.1.0/24

# ICMP timestamp scan 
sudo nmap -sn -PP 192.168.1.0/24

# ICMP mask query scan 
sudo nmap -sn -PM 192.168.1.0/24

# Ping sweep with SYN scan 
sudo nmap -sn -PS22,80,443 192.168.1.0/24

# Ping sweep with ACK scan 
sudo nmap -sn -PA22,80,443 192.168.1.0/24

# Ping sweep with UDP scan 
sudo nmap -sn -PU 192.168.1.0/24

# Save output on file.txt
sudo nmap -sV -oN file.txt 192.168.1.0/24
```

## Scripts

```bash
# Search for Nmap scripts related to ftp
grep "ftp" /usr/share/nmap/scripts/script.db

# Scan with all scripts from vuln category
sudo nmap --script=vuln target-host

# Scan with common scripts. Equivalent to: --script=default
sudo nmap -sC target-host

# Scan for SMB vulnerability
sudo nmap -p 445 --script=smb-vuln* target-host

# Enumerate shares folders and users SMB
sudo nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse target-host

# Enumarate shares folders NFS
nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount target-host
```