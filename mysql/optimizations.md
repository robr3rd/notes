# MySQL Optimizations

## Indexes
- [Convince MySQL to use the right Index](http://code.openark.org/blog/mysql/7-ways-to-convince-mysql-to-use-the-right-index)
	- Thought process outlining 7 ways (from most extreme to more realistic) to convince MySQL to use the most efficient INDEX.

## Disk Space
### Retrieve a sorted list of disk usage per-database per-table
```sql
SELECT 
     table_schema as `Database`, 
     table_name AS `Table`, 
     round(((data_length + index_length) / 1024 / 1024), 2) `Size in MB` 
FROM information_schema.TABLES 
ORDER BY (data_length + index_length) DESC;
```

It likely goes without saying, but the above query is friendly to, say, `WHERE table_schema = 'foo_db_name'` to get results from only one database.
