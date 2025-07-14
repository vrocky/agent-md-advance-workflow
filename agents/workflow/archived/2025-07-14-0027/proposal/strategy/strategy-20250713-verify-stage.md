# Strategy Proposal: Implementation of Separate Verify Stage

## Overview
This strategy outlines the steps to implement a dedicated `verify` stage/command for the file copy tool, ensuring all copied files in the destination are verified against their source counterparts after the copy phase.

## Steps
1. **CLI Extension:**
   - Add a new `verify` command to the CLI (e.g., `python fs_copy_tool/main.py verify --job-dir ... --src ... --dst ...`).
   - Document the command and its options.
2. **Verification Logic:**
   - For each entry in the `destination_files` table (or all files in the destination), find the corresponding source file using `(uid, relative_path)`.
   - Compare the checksum of the destination file to the source file's checksum.
   - If checksums match, mark as verified; if not, log an error and mark as failed in the database.
   - Optionally, support re-verification of all or only failed/unverified files.
3. **Logging and Reporting:**
   - Log all verification results (success, failure, errors) to the job log and update the database with a `verify_status` and `verify_error` field.
   - Provide a summary at the end of the command (e.g., total verified, failed, errors).
4. **Resumability and Idempotency:**
   - The verify stage must be safely repeatable and able to resume from where it left off (using status fields in the database).
5. **Testing:**
   - Add unit and E2E tests to cover the verify stage, including cases with matching, mismatched, and missing files.
6. **Documentation:**
   - Update user and developer documentation to describe the verify stage, its purpose, and usage.

## Rationale
- This approach ensures robust, auditable verification of all copy operations, supports resumability, and provides clear feedback to users and auditors.

---

*Proposed: 2025-07-13*
*Status: Accepted 2025-07-13*
