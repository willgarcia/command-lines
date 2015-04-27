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

postgres - create user
----------------------

```bash
su postgres -c "createdb --encoding UTF8 --template template0 --owner \"$DB_USER\" \"$DB_NAME\""
```

postgres - migrate schema
-------------------------

```bash
# source database
su postgres -c "psql -U postgres -c \"ALTER SCHEMA $FROM_DB_SCHEMA RENAME TO $TO_DB_SCHEMA;\" $FROM_DB_NAME"
su postgres -c "pg_dump $FROM_DB_NAME --inserts --schema $TO_DB_SCHEMA >> $DB_OUTFILE"

# target database
su postgres -c "psql -U postgres -c \"CREATE SCHEMA \"$TO_DB_SCHEMA\" AUTHORIZATION \"$TO_DB_SCHEMA_OWNER\";\" $TO_DB_NAME" >&/dev/null
su postgres -c "psql -U postgres -f $DB_OUTFILE $TO_DB_NAME" >&/dev/null

# target database's ownerships (schemas objects: tables, etc)
su postgres -c "psql -U postgres -c \"ALTER SCHEMA $TO_DB_SCHEMA OWNER TO $TO_DB_SCHEMA_OWNER;\" $TO_DB_NAME"
su postgres -c "psql -U postgres -c \"REASSIGN OWNED BY $FROM_DB_SCHEMA_OWNER TO $TO_DB_SCHEMA_OWNER;\" $TO_DB_NAME"

# migration
su postgres -c "psql -U postgres -c \"ALTER SCHEMA $TO_DB_SCHEMA RENAME TO $FROM_DB_SCHEMA;\" $FROM_DB_NAME"
```


postgres - schema size
----------------------

```sql
SELECT schema_name, 
    pg_size_pretty(sum(table_size)::bigint) as "disk space",
    (sum(table_size) / pg_database_size(current_database())) * 100
        as "percent"
FROM (
     SELECT pg_catalog.pg_namespace.nspname as schema_name,
         pg_relation_size(pg_catalog.pg_class.oid) as table_size
     FROM   pg_catalog.pg_class
         JOIN pg_catalog.pg_namespace 
             ON relnamespace = pg_catalog.pg_namespace.oid
) t
GROUP BY schema_name
ORDER BY schema_name
```
