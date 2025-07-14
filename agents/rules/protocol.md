# Agent Protocols

This document consolidates all protocols and operational rules for agents in this project. These protocols ensure robust, auditable, and context-aware operation and resumability.

---

## Agent Resume Protocol

To ensure robust, auditable, and context-aware resumability, the agent must follow this protocol whenever resuming work after interruption, restart, or handoff:

4. Use CLI tools (e.g., `ls`, `tree`, or platform-specific equivalents) to inspect the current directory structure and file states.
   - On Windows, run:
     ```powershell
     Get-ChildItem -Recurse -File -Name | Where-Object { $_ -notmatch 'venv|pycache|.git|.pytest_cache' }
     ```
     and parse the output to become fully aware of the actual, current file and directory structure. This step is mandatory for every resume.

**Note:** Running the above directory listing command and parsing its output is a required, non-optional step for agent awareness and must be performed every time the agent resumes work. Failure to do so is a protocol violation.

This protocol guarantees that the agent always resumes with full awareness of both the documented and actual state of the project, including all requirements, proposals, CLI structure, and job directory logic, ensuring safe, auditable, and effective continuation of work.

---

## General Rules for Agents

- Any change in plan, workflow, or protocol must be immediately reflected in the relevant workflow files.
- The agent is responsible for keeping all task lists and planning documents up to date and in sync with the current project direction.
- Whenever tests are run, the agent must wait for and review the results before proceeding. All outcomes (pass/fail/errors) must be logged and acted upon as needed.
- After running tests, the agent must:
  1. Wait for test completion and collect all results.
  2. If any test fails, immediately log the failure, analyze the cause, and autonomously attempt to fix the issue before proceeding.
  3. Only continue with new tasks after all tests pass or failures are explicitly deferred with a reason.
- This protocol ensures no test failure is ignored and the agent always follows up until resolution or explicit deferral.
- The agent must autonomously adapt code and tests to ensure all tests can run and pass in any environment, including CI and local development. This includes:
  - Detecting and handling dynamic or temporary test directories as valid resources.
  - Refactoring logic as needed to support robust, environment-agnostic testing.
  - Repeating test/fix cycles until all tests pass or a failure is explicitly deferred with a reason.
- The agent must never pause to ask for permission or confirmation when following up on test failures or required fixes. All test/fix cycles, refactorings, and protocol-driven actions must be performed fully autonomously and logged, without user intervention, until the problem is resolved or explicitly deferred.
- The agent must never narrate or announce future actions. All required test/fix cycles, refactorings, and protocol-driven actions must be performed immediately, in sequence, and fully autonomously, without any intermediate statements or pauses. Only log or report after the fact, not before.

---

## Collaboration and Human + Agent Memory

- Use the `agents/` directory as a **shared memory and planning hub** for all agents and human collaborators.
- When in doubt, document context, reasoning, or choices in the most appropriate `agents/` file.

---

## Best Practices

- **Be explicit:** Every design choice, edge case, and question should be written down.
- **Audit-friendly:** All changes, logs, and state files should be committed as part of the project history.
- **Human-readable:** Prefer Markdown tables, checklists, and clear prose in all `agents/` files.
- **Separation of concerns:** Planning in `agents/`, logs and state in `changes/`, code in `src/`, tests in `tests/`.

---

## File Deletion Protocol

- If a file must be deleted from the repository, create a `delete.sh` script in the `scripts/` directory with the necessary deletion commands.
- Always ask the user to review and run the script manually after verifying its contents.
- Never delete files automatically; all deletions must be explicit and user-approved for safety and auditability.
- The agent will execute `delete.sh` when file deletion is required and, upon successful execution, will empty the contents of `delete.sh` to prevent accidental re-use. Work will then resume as normal.

---

_Last updated: 2025-07-12_
