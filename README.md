# Agent MD Advance Workflow

This repository demonstrates how to organize a GitHub project for advanced AI agent collaboration. All operational rules and protocols are documented under the `agents/` directory. See [AGENTS.md](AGENTS.md) for the high-level index.

---

# AGENTS.md Technique: Project Index & Bootstrap Protocol

## Purpose

The AGENTS.md file now serves as a high-level index and entry point for all agent-related documentation, protocols, and operational rules in the project. Instead of duplicating detailed instructions, it points to authoritative files for each area, ensuring clarity, maintainability, and up-to-date guidance.

## Structure

- **Index:**  
  Provides direct links to key project documents, such as project structure, protocols, and rules.
- **Bootstrap Protocol:**  
  Outlines the mandatory steps for agent context loading and resumption, referencing the canonical sources for each step.
- **Directory Inspection:**  
  Documents the required PowerShell command for inspecting the current directory structure, ensuring agents always operate with full context.

## How to Use

1. **Start with AGENTS.md:**  
   Always begin by reading AGENTS.md when resuming work or onboarding. It tells you where to find the latest project structure, protocols, and rules.
2. **Follow the Index:**  
   Use the provided links to access detailed documentation in the appropriate subdirectories (e.g., project-guildelines.md, protocol.md).
3. **Bootstrap as Instructed:**  
   - List all files using the prescribed PowerShell command.
   - Read all referenced agent-bootstrap.md files.
   - Follow the step-by-step instructions in those files, which will direct you to further details as needed.
4. **Stay Up to Date:**  
   Since AGENTS.md is only an index, always refer to the linked files for the most current and complete information.

## Example Workflow

1. Run the directory inspection command:
   ```powershell
   Get-ChildItem -Recurse -File -Name | Where-Object { $_ -notmatch 'venv|pycache|.git|.pytest_cache' }
   ```
2. Read all agent-bootstrap.md files referenced in AGENTS.md.
3. Follow the instructions in each, which will guide you to the correct protocols and guidelines for your task.

## Benefits

- **Single Source of Truth:**  
  All detailed rules and protocols are maintained in their respective files, reducing duplication and confusion.
- **Easy Onboarding:**  
  New agents and collaborators can quickly find what they need by starting with AGENTS.md.
- **Protocol Compliance:**  
  Ensures every agent or collaborator loads the full project context before acting, as required by project protocols.

