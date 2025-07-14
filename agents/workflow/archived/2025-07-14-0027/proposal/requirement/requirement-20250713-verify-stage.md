# Requirement Proposal: Separate Verify Stage

## Summary
Add a dedicated `verify` stage/command to the file copy tool. This stage will verify the integrity and correctness of all files copied to the destination, ensuring that each file matches its source (by checksum or content) after the copy phase is complete.

## Motivation
- Provides a clear, auditable step to confirm that all copy operations were successful and data integrity is maintained.
- Allows users to re-verify at any time, independent of the copy phase.
- Supports robust, resumable, and trustworthy workflows for critical data migration.

## Protocol Compliance
- The `verify` stage must:
  - Iterate over all files in the destination and compare them to their source counterparts using checksums.
  - Log all results, including any mismatches or errors, to the job log and database.
  - Be resumable and idempotent (can be run multiple times safely).
  - Be available as a separate CLI command (e.g., `verify`).
- All results and failures must be logged and reviewed as per agent protocol.

## Acceptance Criteria
- The `verify` command is available in the CLI and documented.
- The command checks all copied files and logs results.
- The command is robust, platform-agnostic, and cleans up after itself.
- The feature is covered by automated tests.

---

*Proposed: 2025-07-13*
