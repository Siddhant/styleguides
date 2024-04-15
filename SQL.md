- primary key is never defined inline. Always defined as a `constraint` after all the column definitions.
- function names are always in lowercase.

# SQLite
- Always turn on the foreign keys pragma: `PRAGMA foreign_keys = ON;`
  - Rationale: SQLite will silently ignore any foreign key constraints unless we enable this.
- Always use the `STRICT` keyword when declaring tables.
  - Rationale: We want strong typing to be enforced.
