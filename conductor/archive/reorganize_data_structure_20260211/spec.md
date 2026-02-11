# Specification: Organize Data Files by Podcast Title

## Overview
Currently, all data files (e.g., episode metadata JSONs) are saved directly in the `data/` directory. This creates a cluttered flat structure. This feature aims to organize these files by creating a subdirectory for each podcast, named after the podcast's title.

## Functional Requirements

### 1. Directory Structure
- **New Structure:** `<Download Directory>/<Podcast Title>/data/<Filename>`
- **Filename:** The existing filename convention (e.g., `<EpisodeID>.json`) MUST be preserved.
- **Directory Creation:** The application MUST automatically create the directory `<Download Directory>/<Podcast Title>/data` if it does not exist before saving a file.

### 2. Podcast Title Handling
- **Source:** The "Podcast Title" MUST be extracted from the episode's metadata (which the user indicates is available in the data payload).
- **Sanitization:**
    - Any characters in the podcast title that are invalid for file systems (specifically: `/`, ``, `:`, `*`, `?`, `"`, `<`, `>`, `|`) MUST be replaced with an underscore `_`.
    - Example: `Podcast: The Best` -> `Podcast_ The Best`

### 3. Backward Compatibility
- **Existing Files:** Files currently residing in the root `data/` directory MUST NOT be moved or modified automatically. This change applies **only** to newly saved files.

## Non-Functional Requirements
- **Platform:** The path handling MUST be cross-platform compatible (Linux/Windows/macOS), utilizing Python's `pathlib` or `os.path`.

## User Workflow
1. User runs a download command.
2. `xyz-dl` fetches episode data.
3. `xyz-dl` extracts the podcast title.
4. `xyz-dl` sanitizes the title and creates the corresponding folder in `<Download Directory>/<Podcast Title>/data/`.
5. `xyz-dl` saves the JSON file into that folder.
