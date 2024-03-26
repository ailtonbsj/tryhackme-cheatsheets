# OpenSSL

```bash
# Generate password for /etc/passwd
openssl passwd -1 -salt SAL mypass

# Install latest OpenSSL 3.1
sudo apt install build-essential checkinstall zlib1g-dev -y
cd /usr/local/src
sudo wget https://www.openssl.org/source/openssl-3.2.1.tar.gz
sudo tar -xf openssl-3.2.1.tar.gz
sudo rm -rf openssl-3.2.1.tar.gz
cd openssl-3.2.1/
sudo ./config --prefix=/usr/local/ssl --openssldir=/usr/local/ssl shared zlib
sudo make && sudo make test
sudo make install
cd /etc/ld.so.conf.d/
echo "/usr/local/ssl/lib64" | sudo tee openssl-3.2.1.conf
sudo ldconfig -v
openssl version -a
```

[How to isntall OpenSSL in Ubuntu](https://www.golinuxcloud.com/install-openssl-ubuntu/)
