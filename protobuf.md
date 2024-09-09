# General
## Philosophy
- I belive the `.proto` file to be a data dictioanry for your users. Hence, comment as much as you can everywhere. Since data modelling is an art, even docuemnt your desing decisionioning process.

## File formatting
- Use 2 spaces to indent.

# proto2
## File structure
-

## Packages
-

## Message and Field Names 
-

## Required fields
- Never use. All fields must always be `optional`. Rationale: No field is permanent. Yes, even your field contianing primary key. The world keeps evolving, and you never know what field is now suddenly nullable.
  

## Repated fields
- Use pluralized names for repeated fields.
```
repeated string keys = 1;
repeated SubAccount sub_accounts = 17;
```

## Enums
In preivous verison, you can't add the `[deprecated = true]` to an enum value. For those cases, just 

## Deprecated fields
- Must use the `[deprecated = true]` annotation. Unless it is a soft-deprecation; then you can just add a comment.
- Move all deprecated fields to the bottom of your message. They just add noise for your reader.
- If a field has been replaced by a newer field somewhere (same or different message), you must add a comment pointing to the new place:
```
// Deprecated:
optional string account_id = 5;
```

## Date and time

# proto3

# See also
- Protobuf Official Style Guide https://protobuf.dev/programming-guides/style/
