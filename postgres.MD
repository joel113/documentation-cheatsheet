# Postgres Cheatsheet

## Connect

`\l` - Lists all databases
`\c database` - Connect to database
`\dt` - Show tables

## SQL

### Create Table

```
CREATE TABLE [IF NOT EXISTS] table_name (
   column1 datatype(length) column_contraint,
   column2 datatype(length) column_contraint,
   column3 datatype(length) column_contraint,
   table_constraints
);
```
