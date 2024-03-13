## MySQL Server

```bash
# Install MySQL client tool
sudo apt install default-mysql-client

# Conect to database server
mysql -h TARGET-HOST -u root -p

# Gather version of MySQL and OS
mysql> select version();

# List all databases
mysql> show databases;
```

## SQLite3

```bash
# Install SQLite client tool
sudo apt install sqlite3

# Open database
sqlite3 database-in-a-file.db

# Show tables
sqlite> .tables

# Show columns info
sqlite> PRAGMA table_info(my_table);

# List registers
sqlite> SELECT * FROM my_table;
```