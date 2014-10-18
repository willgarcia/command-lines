See [MySQL official documentation](http://dev.mysql.com/doc/) for details.

mysql - privileges
-------

```sql
GRANT USAGE,SELECT ON [db].* TO '[user]'@'%' IDENTIFIED BY '[password]';
FLUSH PRIVILEGES;
```

mysql - database export
-----------------------

```bash
mysqldump -u user -p database | gzip > database.sql.gz
```

mysql - database import
-----------------------

```bash
gunzip < database.sql.gz | mysql -u user -p database
```
