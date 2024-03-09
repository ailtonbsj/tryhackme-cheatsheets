# MySQL Server

```bash
# Install client MySQL tool
sudo apt install default-mysql-client

# Conect to database server
mysql -h TARGET-HOST -u root -p

# Gather version of MySQL and OS
mysql> select version();

# List all databases
mysql> show databases;
```