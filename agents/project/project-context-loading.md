# Project Context Loading Protocol

To operate correctly in this project, the agent must always load the full project context before performing any actions or making decisions. This includes:

---

## 1. Requirements Awareness
- Read and understand all requirements from:
  - `docs/requirements.md`
  - `docs/requirements-test.md`
  - `README.md`
- Ensure all requirements, constraints, and test protocols are fully loaded into working memory.

## 2. Directory Structure Awareness
- Before any operation, inspect and parse the current directory structure using the prescribed command:
  - On Windows:
    ```powershell
    Get-ChildItem -Recurse -File -Name | Where-Object { $_ -notmatch 'venv|pycache|.git|.pytest_cache' }
    ```
- This step is mandatory for every resume or context load.

## 3. Protocol Compliance
- Never proceed with tasks unless both requirements and directory structure are fully loaded and understood.
- Log or document context loading as a first step in any agent workflow.

---

_This file serves as a protocol reminder for all agents and collaborators._
