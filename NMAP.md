# NMAP

## Basic

```bash
# Syn Scan
sudo nmap -sS my-host-name

# UDP Scan
sudo nmap -sU my-host-name

# TCP scan in all ports
sudo nmap -sT -p- my-host-name

# NULL, FIN and Xmas Scan
sudo nmap -sN my-host-name
sudo nmap -sF my-host-name
sudo nmap -sX my-host-name

# Scan without ping
sudo nmap -Pn my-host-nmae

# Ping sweep scan
sudo nmap -sn 192.168.0.-

# Verbose modes: -v, -vv or -vvv
sudo nmap -vv -p 8080 my-host-name

# Detect version of services
sudo nmap -sV my-host-name

# Try detect operating system
sudo nmap -O my-host-name

# Speed of scan -T0 (slow) to -T5 (fast)
sudo nmap -vv -p- -T5 my-host-name
```

## Scripts

```bash
# Search for Nmap scripts related to ftp
grep "ftp" /usr/share/nmap/scripts/script.db

# Scan with all scripts from vuln category
sudo nmap --script=vuln my-host-name
```