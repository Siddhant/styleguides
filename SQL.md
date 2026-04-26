## Tables
- Never give a table the same name as one of its columns and vice versa.
- For reference data tables, always use singular name for your table, rather than plural/collective.
  - Rationale: Reading “SELECT employee.first_name” makes much more sense than “SELECT employees.first_name” / “SELECT staff.first_name”
  - Examples:
    - If you have a table which stores basic refernce data for Banks, name the table `bank`, not `banks`.
    - If you have a table which stores relationships between two financial instruments, name the table `relationship` not `relationships`.
    - A table connecting customers (table `customer`) to their accounts (table `account`) should be called `customer_account` not `customers_accounts`.

## Columns
- Naming:
  - Always use the singular name.
  - Where possible avoid simply using id as the primary identifier for the table.
  - Do not add a column with the same name as its table and vice versa.
  - Always use lowercase except where it may make sense not to such as proper nouns.
- The `check` clause for a column immediately follows a column definition, and always begins on a new line with an additional indentation level.
  ```
  name text not null
    check(length(trim(name)) > 0)
  ```
- A column of type `text`, if defined as `not null`, should always disallow empty strings: `check(length(trim(column_name)) > 0)`
- Uniform suffixes - The following suffixes have a universal meaning ensuring the columns can be read and understood easily from SQL code. Use the correct suffix where appropriate:
  - `_id`—a unique identifier such as a column that is a primary key.
  - `_status`—flag value or some other status of any type such as publication_status.
  - `_total`—the total or sum of a collection of values.
  - `_num`—denotes the field contains any kind of number.
  - `_name`—signifies a name such as first_name.
  - `_seq`—contains a contiguous sequence of values.
  - `_date`—denotes a column that contains the date of something.
  - `_tally`—a count.
  - `_size`—the size of something such as a file size or clothing.
  - `_addr`—an address for the record could be physical or intangible such as ip_addr.


## Priamry Key(s) (PK)
- Specify the primary key first right after the CREATE TABLE statement - even before the column definitions.
- Primary key(s) is never defined inline, even if the PK is just a single column. Always defined as a `constraint`, immediately after all the column definitions.
- The primary key constraint is always named with a prefix, like so: `PK_<table_name>` / `pk_<table_name>`

## Foreign Key(s) (FK)
- The primary key constraint is always named with a prefix, like so: `FK_<table_name>` / `fk_<table_name>`

## Functions
- Function names are always in lowercase.

## SQLite
- Always turn on the foreign keys pragma: `PRAGMA foreign_keys = ON;`
  - Rationale: SQLite will silently ignore any foreign key constraints unless we enable this.
- Always use the `STRICT` keyword when declaring tables.
  - Rationale: We want strong typing to be enforced.

## References
While there are many SQL style guides, here are some I like and have taken inspiration from:
- https://www.sqlstyle.guide
- https://docs.telemetry.mozilla.org/concepts/sql_style
