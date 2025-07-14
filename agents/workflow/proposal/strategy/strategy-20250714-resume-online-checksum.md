# Implementation Strategy: Robust File-Level Resume and Online Checksum for Copy Feature

## Overview
This document outlines the implementation strategy for adding robust file-level resume support and online checksum calculation/verification to the file copy tool.

## Key Steps

1. **File-Level Resume Logic**
   - Track which files have been fully copied in the database (e.g., with a status flag or similar field).
   - On restart, skip files already marked as complete and only copy files that are incomplete or not yet started.
   - There is no need to track or resume at the chunk or byte level within a file.

2. **Copy Logic Enhancement**
   - Update the `copy_file` function to:
     - Copy each file from start to finish in one operation.
     - Calculate and verify checksums for both source and destination as the file is copied.
     - On completion, compare the final checksums and mark the file as complete if they match.
     - If a mismatch is detected, retry the file or flag an error.

3. **CLI and Workflow Integration**
   - Add or update CLI options to support resuming interrupted copies at the file level and reporting online verification status.
   - Ensure the workflow and status reporting commands reflect the new file-level progress and verification data.

4. **Testing**
   - Add/extend automated and manual tests to cover:
     - Interrupted copy and file-level resume scenarios.
     - Online checksum verification during copy.
     - Database state and audit log correctness.

5. **Documentation**
   - Update user and developer documentation to describe the new file-level resume and online verification features.

## Risks & Mitigations
- **Partial/corrupt files:** Always verify checksums before marking a file as complete.
- **Performance:** Use efficient chunk sizes for copying, but do not track chunk-level state.
- **Backward compatibility:** Migrate or handle existing jobs without file-level status fields.

---

**Status:** DRAFT (pending review/approval)
**Date:** 2025-07-14
