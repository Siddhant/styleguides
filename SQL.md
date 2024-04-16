
- Function names are always in lowercase.

# Priamry Key(s) (PK)
- Primary key(s) is never defined inline, even if the PK is just a single column. Always defined as a `constraint`, immediately after all the column definitions.
- The primary key constraint is always named like so: `PK_<table name>`.

# SQLite
- Always turn on the foreign keys pragma: `PRAGMA foreign_keys = ON;`
  - Rationale: SQLite will silently ignore any foreign key constraints unless we enable this.
- Always use the `STRICT` keyword when declaring tables.
  - Rationale: We want strong typing to be enforced.
