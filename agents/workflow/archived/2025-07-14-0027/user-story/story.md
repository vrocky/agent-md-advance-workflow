# User Stories

Document user stories here. Each story should describe a user goal or scenario relevant to the project.

---

## User Story: Robust Two-Stage Verification for File Copy Tool

**Summary:**
As a user, I want the file copy tool to provide a robust, auditable two-stage verification process after copying files, so that I can be confident all files are present, uncorrupted, and match the source.

**Acceptance Criteria:**
- The tool must support a shallow verification stage that checks for file existence, size, and last_modified match.
- The tool must support a deep verification stage that checks file content by recomputing and comparing checksums.
- All verification results must be recorded in dedicated tables for each stage.
- The process must be auditable and results queryable for troubleshooting.
- No schema changes to the main destination_files table.

**Motivation:**
Data integrity and auditability are critical for large-scale file migrations. A two-stage verification process ensures both fast attribute-based checks and deep cryptographic assurance.
