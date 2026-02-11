# Plan: Organize Data Files by Podcast Title

This plan outlines the steps to reorganize the storage of data files by podcast title, ensuring a cleaner directory structure within the `data/` folder.

## Phase 1: Implementation of Path Logic

- [x] Task: Create sanitization utility function
    - [x] Define `sanitize_filename` in `utils.py` to replace invalid filesystem characters with `_`.
    - [x] Add unit tests for `sanitize_filename` (handling characters like `:`, `/`, etc.).
- [x] Task: Update file saving logic to use podcast title subdirectories e28ab8d
    - [x] Modify the data saving function (likely in `downloader.py`) to save in the download directory.
    - [x] Use the sanitized title to construct the destination path: `download_dir/<Sanitized Podcast Title>/data/<EpisodeID>.json`.
    - [x] Ensure the subdirectory is created before saving the file.
- [ ] Task: Conductor - User Manual Verification 'Phase 1: Implementation' (Protocol in workflow.md)

## Phase 2: Verification & Quality Gates

- [x] Task: Verify functionality with a real download
    - [x] Run the CLI to download/fetch an episode.
    - [x] Confirm a new directory `data` is created inside the podcast's download folder.
    - [x] Confirm the JSON file is saved inside that directory.
- [x] Task: Run project quality gates
    - [x] Execute `ruff check .` to ensure linting compliance.
    - [x] Execute `pyright .` to ensure type safety.
- [x] Task: Conductor - User Manual Verification 'Phase 2: Verification' (Protocol in workflow.md)
