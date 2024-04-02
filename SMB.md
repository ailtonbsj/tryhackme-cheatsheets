# SMB and SAMBA

```bash
# Download enum4linux tool
sudo apt install samba-common-bin smbclient ldap-utils polenum
git clone https://github.com/CiscoCXSecurity/enum4linux.git
cd enum4linux && ./enum4linux.pl

# Try get a user list from SMB
./enum4linux.pl -U my-host-name

# Try get a share list from SMD
./enum4linux.pl -S my-host-name

# Enumerate SMB/Samba
./enum4linux.pl -a my-host-name

# Download enum4linux-ng tool
git clone https://github.com/cddmp/enum4linux-ng.git
cd enum4linux-ng && ./enum4linux-ng.py

# Access a public shared folder with smbclient (password: anonymous)
smbclient //some-host-name-or-ip/shared-folder -U anonymous -p 445

# Scan for SMB vulnerability
sudo nmap -p 445 --script=smb-vuln* target-host

# Enumerate shares and users
sudo nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse target-host

# Download shared folder
smbget -R //some-host-name-or-ip/shared-folder
```
