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

## Message and Field Names 
-

## Required fields
- Never use. All fields must always be `optional`. Rationale: No field is permanent. Yes, even your field contianing primary key. The world keeps evolving, and you never know what field is now suddenly nullable.
  

## Repated fields
- Use pluralized names for repeated fields.
```proto
repeated string keys = 1;
repeated SubAccount sub_accounts = 17;
```

## Enums
In preivous verison, you can't add the `[deprecated = true]` to an enum value. For those cases, just 

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

## Common field types
### Date and time
-
### Currency
- Just define a single enum to hold all the ISO-3 currency codes, and swear to yourself to never use anything else for a field meant to hold a currency value. 

# proto3

# See also
- Protobuf Official Style Guide https://protobuf.dev/programming-guides/style/
