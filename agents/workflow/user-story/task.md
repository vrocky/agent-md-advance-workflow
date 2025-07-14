# Tasks

Break down user stories into actionable tasks. Update as tasks are completed or reprioritized.

- [x] Implement dual progress bars (per-file and overall) for the copy phase as per requirement-20250713-dual-progressbar.md
    - [x] Update copy logic to support per-file progress bar (block-wise, logs progress)
    - [x] Update copy logic to support overall progress bar (logs progress)
    - [x] Ensure all progress is logged, not printed
    - [x] Add/Update tests for progress bar feature
    - [x] Document the feature and update requirements checklist

---

## Two-Stage Verification Feature
- [x] Design and create `verification_shallow_results` and `verification_deep_results` tables in the database schema
- [x] Implement shallow verification: check file existence, size, last_modified, and record status for each
- [x] Implement deep verification: recompute and compare checksums, record results
- [x] Update CLI to support both verification stages and result queries
- [x] Add/Update tests for both verification stages
- [x] Document the verification process and update requirements checklist
- [x] Add separate CLI and status commands for shallow and deep verification (summary and full)
- [x] Update manual test script to use new CLI and status commands

---

## Resume and Online Checksum Feature
- [ ] Implement robust file-level resume support for the copy phase
    - [ ] Update copy logic to track which files are fully copied (status flag)
    - [ ] On restart, skip files already marked as complete
    - [ ] Add/Update tests for file-level resume scenarios
- [ ] Implement online checksum calculation and verification
    - [ ] Calculate and compare running checksums for each file during copy
    - [ ] Retry or flag error on checksum mismatch
    - [ ] Store file status and checksums in the database for auditability
    - [ ] Add/Update tests for online verification
- [ ] Update CLI and workflow to support file-level resume and online verification features
- [ ] Update documentation and requirements checklist
