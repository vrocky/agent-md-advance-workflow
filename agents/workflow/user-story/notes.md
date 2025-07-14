# User Story Notes

Use this file for notes, clarifications, and discussions related to user stories and tasks.

---

## Notes on Two-Stage Verification Feature
- Shallow verification is fast and checks for basic file attributes (existence, size, last_modified, etc.)
- Deep verification is slower but provides cryptographic assurance by comparing checksums
- Each stage has its own results table for auditability and extensibility
- No changes are made to the main destination_files table schema
- CLI should allow running either or both stages and querying results
