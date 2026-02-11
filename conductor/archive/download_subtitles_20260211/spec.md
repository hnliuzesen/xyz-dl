# Specification - Subtitle Download Feature

## Overview
This track adds the ability to download subtitles (transcripts) for Xiaoyuzhou FM episodes. Subtitles are fetched via a specific API and saved as JSON files alongside the media or metadata.

## Functional Requirements
1.  **Subtitle Retrieval**:
    -   Fetch transcript metadata using `POST https://api.xiaoyuzhoufm.com/v1/episode-transcript/get`.
    -   Payload must include `eid` and `mediaId` (from `episode.media.id`).
    -   Extract `transcriptUrl` from the response.
2.  **Subtitle Download**:
    -   Download the JSON subtitle file from `transcriptUrl`.
    -   Use specific headers for the download request:
        -   `Host: transcript-highlight.xyzcdn.net`
        -   `Accept: application/json`
        -   `User-Agent: Xiaoyuzhou/2.99.1(android 28)`
3.  **File Naming and Storage**:
    -   Save subtitles with the same base name as the audio file, appended with `.subtitle.json` (e.g., `001. Title.subtitle.json`).
    -   Store the subtitle file in the same directory as the audio file.
4.  **CLI Integration**:
    -   Add a `--with-subtitles` flag to enable subtitle downloading.
    -   **Opt-in Logic**: Subtitles are NOT downloaded by default.
    -   **Save-Only Support**: If `--save-only` and `--with-subtitles` are both used, download subtitles and save metadata without the audio file.
    -   Support subtitle download for single episodes, podcast lists, and from JSON inputs.

## Non-Functional Requirements
-   **Robustness**: Handle cases where an episode does not have subtitles (the API might return an error or empty data).
-   **Efficiency**: Reuse existing download logic/session patterns where possible, while adhering to the specific header requirements for transcript CDNs.

## Acceptance Criteria
-   [ ] Running `python main.py <id> --with-subtitles` downloads both audio and the `.subtitle.json` file.
-   [ ] Running `python main.py <id> --save-only --with-subtitles` downloads the `.subtitle.json` file and saves metadata, but no audio.
-   [ ] Subtitle files are correctly named and placed in the podcast's download directory.
-   [ ] The feature handles episodes without subtitles gracefully (e.g., skip with a warning).

## Out of Scope
-   Conversion to other formats (SRT, VTT).
-   Automatic translation of subtitles.
