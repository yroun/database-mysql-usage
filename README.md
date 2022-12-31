# Checking MySQL Usage

Check the used capacity size of MySQL tables

## The size of one table in one database

```
SELECT
    TABLE_NAME AS `Table`,
    ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE
      TABLE_SCHEMA = "database_name"
  AND
      TABLE_NAME = "table_name"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

## All table sizes in one database

```
SELECT
    TABLE_NAME AS `Table`,
    ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "database_name"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

## All table sizes for all databases

```
SELECT
    TABLE_SCHEMA AS `Database`,
    TABLE_NAME AS `Table`,
    ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```
