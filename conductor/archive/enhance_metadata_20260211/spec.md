# Specification - Enhance Metadata Retrieval

## Overview
This track aims to improve how users interact with retrieved host and podcast information. Instead of just raw output, the CLI will provide formatted tables for readability and automatically save metadata locally alongside any downloads.

## Functional Requirements
- **Table Output:** Implement formatted table displays for host, podcast, and episode metadata using a library or manual formatting.
- **Metadata Persistence:** Automatically save metadata in Markdown and JSON formats when an entity is retrieved or an episode is downloaded.
- **Custom Directory Support:** Ensure metadata is saved in the user-specified download directory.

## Acceptance Criteria
- Running a command to fetch host info displays a clean table in the terminal.
- Fetching info or downloading content results in a `.json` and `.md` file being created in the destination folder containing all relevant metadata.
