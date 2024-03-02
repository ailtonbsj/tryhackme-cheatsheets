# TryHackMe Cheatsheets and Write-ups

Some stuffs learned in war rooms from TryHackMe platform.

## VPN

```bash
# Install OpenVPN tool
sudo apt install openvpn

# Connect to a VPN
sudo openvpn your-vpn-file.ovp
```

## Steganography

```bash
# Install StegHide tool
sudo apt install steghide

# Hide a secret into a picture (pic.jpg will be replaced)
steghide embed -cf pic.jpg -ef secret.txt

# Display info about a file whether it has embedded secrets
steghide info pic.jpg

# Extract secret from a picture
steghide extract -sf pic.jpg
```

[Steganography - A list of useful tools and resourcesPermalink](https://0xrick.github.io/lists/stego/)

[Steghide Documentation](https://steghide.sourceforge.net/)

## Vulnerabilities and Exploits

```bash
# Download searchsploit tool
git clone https://gitlab.com/exploit-database/exploitdb.git
cd exploitdb && ./searchsploit -h

# Search for exploits samples
./searchsploit fuel cms
./searchsploit proftpd 1.3.5
```

[Exploit Database](https://www.exploit-db.com/)

[National Vulnerability Database](https://nvd.nist.gov/vuln/search)

[CVE Mitre](https://cve.mitre.org/)

## Find files on Linux

```bash
# Find by filename
find / -name passwords.txt

# Find by extension
find / -iname *.txt

# Fast way to find files
locate passwords.txt
```

## NMAP Basic

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

## NMAP Scripts

```bash
# Search for Nmap scripts related to ftp
grep "ftp" /usr/share/nmap/scripts/script.db

# Scan with all scripts from vuln category
sudo nmap --script=vuln my-host-name
```

## SMB and SAMBA

```bash
# Download enum4linux tool
sudo apt install samba-common-bin smbclient ldap-utils polenum
git clone https://github.com/CiscoCXSecurity/enum4linux.git
cd enum4linux && ./enum4linux.pl

# Download enum4linux-ng tool
git clone https://github.com/cddmp/enum4linux-ng.git
cd enum4linux-ng && ./enum4linux-ng.py

# Try get a user list from SMB
./enum4linux.pl -U my-host-name

# Try get a share list from SMD
./enum4linux.pl -S my-host-name

# Enumerate SMB/Samba
./enum4linux.pl -a my-host-name

# Access a public shared folder with smbclient (password: anonymous)
smbclient //some-host-name-or-ip/shared-folder -U anonymous -p 445
```

## Dumping network traffic

```bash
# Dumping ICMP packages from VPN interface
sudo tcpdump ip proto \\icmp -i tun0
```

## Metasploit Framework

```bash
# Install GPG key from Metaploit repository
sudo wget https://apt.metasploit.com/metasploit-framework.gpg.key \
-O /etc/apt/trusted.gpg.d/metasploit.asc

# Install Metaploit repository
echo "deb https://apt.metasploit.com xenial main" | \
sudo tee /etc/apt/sources.list.d/metasploit.list

# Install Metaploit framework
sudo apt list metasploit-framework
```