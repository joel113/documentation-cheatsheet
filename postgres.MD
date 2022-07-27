# Postgres Cheatsheet

## Connect

`\l` - Lists all databases
`\c database` - Connect to database
`\dt` - Show tables
`\d+ table_name` - Show table definition

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

## Upsert

```
INSERT INTO table_name(column_list)
VALUES(value_list)
ON CONFLICT target action;
```

The target can be one of the following:

- `(column_name)` - a column name
- `ON CONSTRAINT contraint_name` - a constraint name
- `WHERE predicate` - a predicate

The action can be one of the following:

- `DO NOTHING` - which means that nothing should be done if the row already exists in the table
- `DO UPDATE SET column1 = value1, ... WHERE condition` - which means that some fields are updated
