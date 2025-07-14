# AGENTS.md

## Index

- [Project Overview and Structure](agents/project/project.md)
- [Agent Protocols and Rules](agents/rules/protocol.md)

---

This file now serves as a high-level index. All detailed project information, protocols, and operational rules have been moved to their respective files for clarity and maintainability.

- For project structure, best practices, and collaboration guidelines, see `agents/project/project.md`.
- For all agent protocols and operational rules, see `agents/rules/protocol.md`.

Refer to these files for the most up-to-date and complete documentation.

---

## Directory Inspection for Resume

To inspect the current directory structure and file states on Windows, run the following PowerShell command:

```powershell
Get-ChildItem -Recurse -File -Name | Where-Object { $_ -notmatch 'venv|pycache|.git|.pytest_cache' }
```

Parse the output to become fully aware of the actual, current file and directory structure. This step is mandatory for every resume.

---

## Generic Agent Bootstrap Algorithm

1. List all files in the project directory (excluding venv, pycache, .git, .pytest_cache) using the following PowerShell command:

   ```powershell
   Get-ChildItem -Recurse -File -Name | Where-Object { $_ -notmatch 'venv|pycache|.git|.pytest_cache' }
   ```

2. Read the contents all agent-bootstrap.md files.
3. Follow the instructions in `agent-bootstrap.md` to bootstrap the agent, step by step, as described in the document.
4. Execute each step in order, ensuring all requirements and setup tasks are completed before proceeding to the next.
5. Repeat the process for any additional bootstrap or setup instructions found in other relevant documentation files.

_Last updated: 2025-07-13_
