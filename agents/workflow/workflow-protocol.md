# Project Workflow Protocol

This directory contains the canonical workflow protocol documentation for the project. The structure is as follows:

- `proposal/requirement/` — Requirement proposals (one file per proposal)
- `proposal/strategy/` — Implementation strategies (one file per strategy)
- `proposal/status.md` — Status tracking for all proposals
- `user-story/story.md` — User stories
- `user-story/task.md` — Tasks derived from user stories
- `user-story/notes.md` — Notes and clarifications
- `user-story/other.md` — Other user story artifacts
- `archived/` — Archived workflow and planning files (date-stamped)

---

## Workflow Rules and Protocols

### Collaboration and Human + Agent Memory

- Use the workflow directory as a **shared memory and planning hub** for all agents and human collaborators.
- When in doubt, document context, reasoning, or choices in the most appropriate file.
- Move resolved items from questions to notes or decisions as appropriate.

---

### Best Practices

- **Be explicit:** Every design choice, edge case, and question should be written down.
- **Audit-friendly:** All changes, logs, and state files should be committed as part of the project history.
- **Human-readable:** Prefer Markdown tables, checklists, and clear prose in all workflow files.
- **Separation of concerns:** Planning in workflow, logs and state in `changes/`, code in `src/`, tests in `tests/`.

---

### Codebase Cleanliness and Redundancy

- Whenever new code or modules are added, ensure any old, redundant, or superseded files are removed or cleaned up immediately.
- The codebase must remain free of duplicate or obsolete files at all times.
- Refactor and consolidate logic as the project evolves to maintain clarity and maintainability.

---

### Requirements Checklist

- All requirements mentioned in the `/docs/` directory must be tracked in a running checklist in this workflow.
- Each item is marked complete only after full implementation and verification.
- The checklist must be updated as requirements evolve or new ones are added.
- Use this checklist for audit, review, and milestone tracking.

---

### Micro-Task Tracking & Autonomous Operation Protocol

- All micro-tasks, sub-steps, and atomic actions must be logged in a running checklist to ensure nothing is forgotten.
- The agent must work fully autonomously, tracking every step and sub-step, and never omitting required actions or context.
- Use the checklist as a running log for granular progress.

---

### Proposal Refinement Protocol

- During the proposal refinement stage, only update the proposal file with clarifications, discussion, and refinements.
- The agent must present each new proposal draft to the user and explicitly ask for feedback or refinements.
- The agent must continue to iterate and refine the proposal based on user feedback, and only proceed after explicit user approval.
- Do not update requirements or task files until the proposal is explicitly marked as "Accepted" or "Ready for implementation" in the proposal file.
- Once accepted, proceed to update all other documentation and begin implementation.
- This ensures a clear separation between proposal refinement and implementation, preventing confusion or premature changes.

---

### Proposal Refinement and User Story Chronology Protocol

- During the proposal refinement stage, only update the proposal file with clarifications, discussion, and refinements.
- The agent must present each new proposal draft to the user and explicitly ask for feedback or refinements.
- The agent must continue to iterate and refine the proposal based on user feedback, and only proceed after explicit user approval.
- **User stories, tasks, and notes must NOT be created or updated until the proposal is explicitly marked as "Accepted" or "Ready for implementation" in the proposal file.**
- Once the proposal is accepted, immediately proceed to update the user story, task, and notes files to reflect the approved requirements and implementation plan.
- This strict chronology ensures that user stories and tasks always reflect only approved requirements, and prevents premature or out-of-order documentation.

---

### Unified Archival Protocol for Proposals and User Stories

- When a proposal (requirement or strategy) or a user story (with its tasks and notes) is marked as "Complete":
  - The agent must immediately archive the full file(s) into the appropriate `archived/YYYY-MM-DD-HHMM/` directory, using the current date and time.
  - **Archival must be performed by running the provided archival script (`archive_agents.sh` or `archive_agents.ps1`) in the `scripts/` directory.** Manual copying or deletion is not permitted; files must be moved using these scripts to ensure traceability and protocol compliance.
  - For proposals, update `proposal/status.md` to reflect the new status as "Complete". For user stories, update the relevant checklist or status table to reflect completion.
  - The agent must then **delete the original file(s)** from the active `proposal/requirement/`, `proposal/strategy/`, or `user-story/` directories, so only active (incomplete) items remain. This deletion is performed as part of the archival script.
  - The archival and deletion action must be logged in the commit message or workflow log for traceability.
- Archival and deletion are mandatory and must be performed as soon as a proposal or user story is closed as complete. Failure to archive and delete using the provided script is a protocol violation.
- The archival and deletion process must be visible and explicit in the agent's workflow, with clear steps and confirmation.
- This ensures both proposals and user stories follow the same, crystal-clear archival process for a clean, auditable, and focused workflow.

---

## Archival Protocol

- After each major commit, milestone, or significant work session, all workflow and planning `.md` files in this directory must be archived.
- Archive location: `archived/YYYY-MM-DD-HHMM/` (date and time-stamped).
- Only the current, active `.md` files remain in the workflow directory for the next session—reset to template/heading state.
- Archival is performed via scripts (e.g., `archive_agents.sh` and `archive_agents.ps1`) in the `scripts/` directory.
- The agent or user must run the archival script after each major commit.
- This ensures a clean, focused workspace for new work, and a full, immutable history for audit and review.

---

### Requirement Proposal Content Protocol

- Requirement proposals must focus strictly on the technical, user-facing, and functional requirements of the feature or change being proposed.
- References to workflow process, chronology, or protocol enforcement should not be included in the requirement proposal itself.
- All workflow and process rules are to be documented and enforced exclusively in the workflow protocol documentation.
- This ensures that requirement proposals remain clear, concise, and focused on the feature, while process compliance is managed separately.

---

### Proposal Approval and User Story Creation Protocol

- Once a requirement proposal is reviewed and approved by the user, its status must be immediately updated to "Accepted" or "Ready for implementation" in the proposal file and in `proposal/status.md`.
- Only after this status update is performed may the agent proceed to create or update user stories, tasks, and notes reflecting the approved requirements.
- This step must be explicit and auditable, ensuring that user stories and tasks are always based on approved proposals and never created prematurely.
- The agent must log or document the approval and status change as part of the workflow.

---

_Last updated: 2025-07-12_
