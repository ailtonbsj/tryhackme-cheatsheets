# Network Scanning

## APRN Scan

```bash
# Install arp-can tool
sudo apt install arp-scan

# Scan all your local netwrok
sudo arp-scan -l

# Scan another network
sudo arp-scan 192.168.2.1/24

# Install masscan tool
sudo apt install masscan

# Scan with Syn packages
masscan MACHINE_IP/24 -p80,443
```

## Dumping network traffic

```bash
# Dumping ICMP packages from VPN interface
sudo tcpdump ip proto \\icmp -i tun0
```