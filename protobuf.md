# General
## Philosophy
- I belive the `.proto` file to be a data dictioanry for your users. Hence, comment as much as you can everywhere. Since data modelling is an art, even docuemnt your desing decisionioning process.

## Project structure
```
project-root/
  build.gradle
  src/
    main/
      java/
        - useful java utils for working with your protos
      proto/
        enums/
          - all .proto files for enums
        - all .proto files
      resrouces/
    test/
      java/
        - test classes for your generated java from .proto files
      proto/
        - .proto files required for testing-only
      resources/
```

## File formatting
- Use 2 spaces to indent.

# proto2
## File structure
- All files should be ordered in the following manner:
1. License header (if applicable)
2. Authors
3. Date-of-file-creation 
4. File overview
5. Syntax
6. Package
7. Imports (sorted)
8. File options
9. Everything else

- Alwyas start with an author and date-of-file-creation section:
```proto
// Author: Siddhant Saraf (Siddhant.Saraf@abc.com)
// Author: Mickey Mouse (mickey@disney.com)
// Date: August 2023
```

Rationale: Data modelling is an art, and any canvas should always have its author's signature. Hence, if you are migrating protos across files, carry over the Author names please - pay respect to the giants whoe shoulders you are sitting on!

- TODO

## Packages
-

## File Options
- Always enable the Java multiple files option, even if (today!) you have only one message in the file:
```proto
option java_multiple_files = true;
```
- also add:
```proto
option java_package = "com.example.tutorial.protos";
option java_outer_classname = "AddressBookProtos";
```

## Message and Field Names 
- Don't use suffixes like "Details", "Info", etc. in message names:
```proto
message AccountInfo { // just name this "Account"
message CardDetails { // just name this "Card"
```
Rationale: It's redundant - all messages contain details/info of _something_.

## Required fields
- NEVER use. All fields must always be `optional`. Rationale: No field is permanent. Yes, even your field contianing primary key. The world keeps evolving, and you never know what field is now suddenly nullable.
  

## Repated fields
- Use pluralized names for repeated fields.
```proto
repeated string keys = 1;
repeated SubAccount sub_accounts = 17;
```

## Enums
- Always put an enum inside a message. While protobuf allows you to define "bare" (gloabl) enums, these enums are known to cause an issue - if they are imported into other files, they will start interfering with other enum values. See this StackOverflow[https://stackoverflow.com/questions/27030332/solutions-to-resolve-enum-field-naming-restriction-in-google-protobuf-due-to-c] for more details.
- Its not always necessary to for enum values to be sorted alphabetically. Some developers find it useful, some find it useless work. It's left to the develoep's preference. However, if you are adding new values to an existing enum, respect the convention being followed. 
- In preivous verisons of the protobuf compiler (`protoc`), you can't add the `[deprecated = true]` to an enum value. For those cases, just add a comment:
```proto
enum MyEnum {
  MY_ENUM_UNSPECIFIED = 1;
  OLD_VLUE = 2; // deprecated; use OLD_VALUE instead; Reason: was a typo
  OLD_VALUE = 3;
}
```

## Deprecated fields
- Must use the `[deprecated = true]` annotation. Unless it is a soft-deprecation; then you can just add a comment.
- Move all deprecated fields to the bottom of your message. They just add noise for your reader.
- Must add a **reason** for deprecation. This is non-negotiable!
- If a field has been replaced by a newer field somewhere (same or different message), you must add a comment pointing to the new place:
```proto
// The unique identifier for this account.
optional string account_no = 12;
// The unique identifier for this account.
// Deprecated: Repalced by field 'account_no' (#12). Reason: Our upstream has started using alphabets in the account identifer since May 2012.
optional int64 account_id = 5;
```

## Data Modelling tips and tricks
- For entity-entity relationships, do not add "relationship" attribtues inside the "entity" message. Instead create a _new_ "Relationship" message to contain the parameters of the relationship between the two entities.
```proto
// TODO improve this exmaple, it's not the best right now
message Comapny {}
message Preson {}
message ComapnyPersonRealtionship {
  optional Date employment_start_date = 1;
  optional Date employment_end_date = 2;
}
```

## Common field types
### Date and time
-
### Currency
- Just define a single enum to hold all the ISO-3 currency codes, and swear to yourself to never use anything else for a field meant to hold a currency value.
- Define a separate enum for virtual currencies.

## Refactoring
- Or if you have mistakenly added an unrelated message to your `.proto` file, you'll want to move a message to a different/new file. Here is how to do this safely:
  - TODO move to a new file
  - TODO move to an existing file
- If your `.proto` files becomes too long, you'll find yourself wanting to split it into multiple files. Here is how to do this safely:
  - TODO maybe this is same as above ? if yes, merge it

# proto3

# See also
- Protobuf Official Style Guide https://protobuf.dev/programming-guides/style/
