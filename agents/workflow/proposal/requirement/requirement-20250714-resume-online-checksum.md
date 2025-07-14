# Requirement Proposal: Robust File-Level Resume and Online Checksum for Copy Feature

## Summary
The file copy tool must support robust, auditable resume functionality for interrupted copies at the file level, and perform online checksum calculation and verification during the copy process. This ensures data integrity and reliability, even in the event of interruptions or failures.

## Motivation
- Users need to safely resume large or long-running copy operations after interruption (e.g., crash, power loss, network failure).
- Data integrity must be guaranteed by verifying checksums as files are copied, not just after the fact.

## Requirements
1. **File-Level Resume Support**
   - The copy process must track which files have been fully copied.
   - On restart, the tool must skip already completed files and only copy files that are incomplete or not yet started.
   - There is no need to track or resume at the chunk or byte level within a file.
2. **Online Checksum Calculation and Verification**
   - As each file is copied, calculate a running checksum (e.g., SHA256) for both source and destination.
   - On completion of each file, verify the final checksums match and record them in the database.
   - If a mismatch is detected, retry the file or flag an error.
3. **Auditability**
   - All file copy status and checksum data must be stored for auditability.

## Acceptance Criteria
- Copy operations can be safely resumed after interruption, with no data loss or corruption, at the file level.
- Online checksum verification is performed during copy, not just after.
- All actions and state are logged and auditable, with file status and checksums kept in the database.
- The feature is covered by automated and manual tests.

---

**Status:** DRAFT (pending review/approval)
**Date:** 2025-07-14
