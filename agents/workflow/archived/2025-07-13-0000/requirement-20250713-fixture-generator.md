# Requirement Proposal: Simple, Planned-Structure Fixture Generator

## Title
Simple Fixture Generator with Planned Source and Destination Directory Structures for Manual Browsing

## Date Proposed
2025-07-13

## Motivation
- Manual and agent-driven testing is easier when both source and destination directory structures are predictable and easy to browse.
- Clear separation of source and destination directories allows for straightforward comparison and verification of file operations.

## Description
- Implement a fixture generator script that:
  - Creates two top-level directories: one for the source, one for the destination
  - Each directory contains a planned, human-readable tree (e.g., folder1, folder2, file1.txt, file2.txt)
  - Allows configuration of depth, width, and number of files per folder for both source and destination
  - Optionally adds a few duplicate files in the source for basic duplicate detection
  - The destination directory may be empty or contain a subset of files for testing copy/skip logic
- The structure should be easy to navigate and visually inspect in a file browser or terminal.
- No need for complex edge cases or special file types in this first version.

## Acceptance Criteria
- The fixture generator script exists and is documented.
- It creates two predictable, planned directory trees (source and destination) for easy manual browsing.
- The structure and contents are easy to verify by inspection and comparison.
- The script is included in the repository and referenced in test documentation.

## Status
Complete

---

*Refined by agent on 2025-07-13, archived on completion*
