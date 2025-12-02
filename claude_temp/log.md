
#BUILT-IN LOGGING
ALWAYS include logging in generated code:

Required Logging Points:
- Function entry/exit (non-trivial functions)
- File I/O, network requests, parsing operations
- Data transformations (input/intermediate/output)
- Conditional branches, loop progress
- All errors and exceptions

Implementation:
- Use proper logging library (logging, log4j, etc.)
- Setup: File + console output, configurable levels
- Add --verbose/--debug CLI flag
- Log BEFORE risky operations
- Include context: operation, data values, state

Format:
[TIMESTAMP] [LEVEL] [FUNCTION] Message + relevant data

Benefits for debugging:
- User can see exactly where code fails
- Variable values at failure point visible
- Execution path traceable
- Intermediate results verifiable
