
- Function names are always in lowercase.
- The `check` clause for a column always begins on a new line, with an additional indentation level.

# Columns
- Unless really required, columns names should be lowercase.

# Priamry Key(s) (PK)
- Primary key(s) is never defined inline, even if the PK is just a single column. Always defined as a `constraint`, immediately after all the column definitions.
- The primary key constraint is always named with a prefix, like so: `PK_<table_name>` / `pk_<table_name>`

# Foreign Key(s) (FK)
- The primary key constraint is always named with a prefix, like so: `FK_<table_name>` / `fk_<table_name>`

# SQLite
- Always turn on the foreign keys pragma: `PRAGMA foreign_keys = ON;`
  - Rationale: SQLite will silently ignore any foreign key constraints unless we enable this.
- Always use the `STRICT` keyword when declaring tables.
  - Rationale: We want strong typing to be enforced.
