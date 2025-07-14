# Proposal: Verification Table and Two-Stage Verification Process

## Motivation

The current approach alters the `destination_files` table to add verification status columns. This is not ideal for the following reasons:
- Schema changes are intrusive and can cause migration issues.
- Verification is a distinct process and should be tracked separately for auditability and extensibility.
- Different types of verification (shallow, deep, future types) should each have their own dedicated table for clarity and separation of concerns.

## Proposal

### 1. Separate Verification Tables by Type
- Create a new table for each verification type, e.g.:
  - `verification_shallow_results`
  - `verification_deep_results`
- Each row records:
  - `uid` (volume ID)
  - `relative_path`
  - For shallow: status fields for each check (see below)
  - For deep: checksum verification status
  - `timestamp`

### 2. Two-Stage Verification
- **Stage 1: Shallow Verify (Basic Attribute Checks)**
  - For each file expected at the destination (with `copy_status='done'`):
    - Check if the file exists at the destination.
    - Check if file size matches source.
    - Check if last_modified matches source.
    - Optionally check permissions, ownership, etc.
    - Record status for each check: e.g., `exists`, `size_matched`, `last_modified_matched`, etc.
    - Overall `verify_status` is 'ok' only if all checks pass; otherwise, record which checks failed.
    - Results go in `verification_shallow_results`.
- **Stage 2: Deep Verify (Checksum)**
  - For all files present at the destination:
    - Recompute and compare checksums between source and destination.
    - Mark as 'ok' if checksums match, 'failed' if not, and record error details.
    - Results go in `verification_deep_results`.

### 3. Protocol
- Each verification stage logs results in its own table.
- The tool can be run in either mode or both, with results queryable for audit and troubleshooting.
- No schema changes to `destination_files`.

### 4. Benefits
- Clean separation of concerns.
- Easier to extend verification logic in the future (add new tables for new verification types).
- Full audit trail of all verification runs and results, organized by type.
- Shallow verification provides fast, attribute-based confidence; deep verification provides cryptographic assurance.

---

## Next Steps
- Update CLI and implementation to use separate tables for each verification type and the two-stage process.
- Update requirements and documentation after review.
