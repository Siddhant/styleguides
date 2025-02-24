- When encountering an eroor, small/short methods/functions should always throw exceptions (for example `parseDate`), while high level methods should log the errors/warnings and try to recover from the exception and try to complete the job as much as they can. This is because the lowest function in the call stack has no context on how to handle the exeption. 
Further, the short method should not log any errros/warrings - it should just pass on the error message to it's caller by puttin the message inside an exception.

# Testing
## Unit tests
- Never test private methods.
- Measure progress of unit tests using jacoco's "Instruction Coverage" metric.
