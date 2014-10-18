See [Postgres official documentation](http://www.postgresql.org/docs/) for details.

postgres - drop all functions pg, per sschema
---------------------------------------------

```sql
SELECT 
    'DROP FUNCTION ' || ns.nspname || '.' || proname || '(' || oidvectortypes(proargtypes) || ');'
FROM 
    pg_proc 
INNER JOIN 
    pg_namespace ns ON (pg_proc.pronamespace = ns.oid)
WHERE 
    ns.nspname = 'my_schema'
ORDER BY
    proname
;
```


postgres - drop/truncate a list of table (plsql function)
---------------------------------------------------------

```sql
CREATE OR REPLACE FUNCTION drop_tables(_schema text)
  RETURNS void AS
$func$
BEGIN
   EXECUTE (
      SELECT 'DROP TABLE '
             || string_agg(quote_ident(t.tablename), ', ')
             || ' CASCADE'
      FROM   pg_tables t
      WHERE  t.schemaname = _schema
   );
END
$func$ LANGUAGE plpgsql;
SELECT drop_tables('public');
```

postgres - database dump
------------------------

```bash
pg_dump -Ft base_name > /path/base_name.tar
```

postgres - database restore
---------------------------

```bash
pg_restore -Ft /path/base_name.tar -d base_name
```
  
postgres - kill database sessions
---------------------------------

```sql
SELECT 
    pg_terminate_backend(pg_stat_activity.pid)
FROM 
    pg_stat_activity
WHERE 
    pg_stat_activity.datname = 'databaseName'
;
```

