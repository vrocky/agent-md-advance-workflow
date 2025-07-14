# Requirement Proposal: E2E Test for Import Checksums Feature

## Summary
Add an end-to-end (E2E) test to verify the `import-checksums` feature of the file copy tool. This test will ensure that checksums can be correctly imported from an old database into a new job and that the imported checksums are used as expected in subsequent operations.

## Motivation
- The `import-checksums` feature is critical for resumability and migration from previous jobs.
- No E2E test currently covers this workflow, so regressions or integration issues may go undetected.
- Ensures protocol compliance and robust, auditable operation.

## Protocol Compliance
- The E2E test must:
  - Set up a source and destination with files.
  - Create an "old" database with checksums.
  - Use the CLI to import checksums into a new job.
  - Verify that the imported checksums are present and correct in the new database.
  - Be fully automated and repeatable.
- All results and failures must be logged and reviewed as per agent protocol.

## Acceptance Criteria
- The E2E test is present in `e2e_tests/` and runs as part of the standard test suite.
- The test passes if and only if the imported checksums are correctly reflected in the new job database.
- The test is robust, platform-agnostic, and cleans up after itself.

---

*Proposed: 2025-07-13*
*Status: Accepted 2025-07-13*
