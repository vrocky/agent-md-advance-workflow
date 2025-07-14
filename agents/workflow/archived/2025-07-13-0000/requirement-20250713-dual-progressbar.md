# Requirement Proposal: Dual Progress Bars for Copy Phase

## Summary
Implement two progress bars during the copy phase:
- **Per-file progress bar:** Shows the progress of the current file being copied (block-wise).
- **Overall progress bar:** Shows the progress of the entire copy operation (number of files copied out of total).

## Motivation
- Improves user feedback and transparency during long copy operations.
- Helps diagnose performance issues and track large file copies.
- Aligns with best practices for auditability and user experience.

## Protocol Compliance
- Both progress bars must log progress via the Python logging module (not print).
- All operations must remain resumable, idempotent, and safely interruptible.
- No protocol, requirements, or testing rules may be violated.
- Feature must be fully tested and documented.

## Acceptance Criteria
- Per-file progress bar logs progress for each file as it is copied (block-wise, e.g., every 10%).
- Overall progress bar logs progress for the entire copy operation.
- No duplicate or obsolete files are introduced.
- All new code is covered by tests and passes lint/type checks.

---

*Proposed: 2025-07-13*
*Status: Complete 2025-07-13*
