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

# Extract secrect from a picture
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