
- Function names are always in lowercase.
- The `check` clause for a column always begins on a new line, and with an additional indentation level.
  ```
  name text not null
    check(length(trim(name)) > 0)
  ```
- xxx

# Tables
- For reference data tables, always use singular name for your table, rather than plural/collective.
  - Rationale: Reading “SELECT employee.first_name” makes much more sense than “SELECT employees.first_name” / “SELECT staff.first_name”
  - Examples:
    - If you have a table which stores basic refernce data for Banks, name the table `bank`, not `banks`.
    - If you have a table which stores relationships between two financial instruments, name the table `relationship` not `relationships`.
    - A table connecting customers (table `customer`) to their accounts (table `account`) should be called `customer_account` not `customers_accounts`.

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

# References
While there are many SQL style guides, here are some I like and have taken inspiration from:
- https://www.sqlstyle.guide
- https://docs.telemetry.mozilla.org/concepts/sql_style
