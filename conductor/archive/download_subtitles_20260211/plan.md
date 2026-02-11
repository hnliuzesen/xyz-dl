# Implementation Plan - Subtitle Download Feature

## Phase 1: API and Core Logic
- [x] Task: Implement `get_episode_transcript` in `api.py`. 4f23ae4
    - [x] Add a new method to `XiaoyuzhouAPI` to POST to `v1/episode-transcript/get`.
    - [x] Ensure it accepts `eid` and `mediaId`.
- [x] Task: Add subtitle download logic to `XiaoyuzhouDownloader` in `downloader.py`. 4f23ae4
    - [x] Implement a `download_subtitle` method that uses the specific headers for the xyzcdn.net host.
    - [x] Implement logic to generate the `.subtitle.json` filename.
- [x] Task: Conductor - User Manual Verification 'Phase 1: API and Core Logic' (Protocol in workflow.md)

## Phase 2: Integration with Download Flows
- [x] Task: Update `download_episodes_sequential` in `downloader.py`. 4f23ae4
    - [x] Add logic to check for the subtitle flag and trigger `download_subtitle`.
- [x] Task: Update `download_single_episode` in `downloader.py`. 4f23ae4
    - [x] Add logic to support subtitle downloading, including when `save_only` is True.
- [x] Task: Conductor - User Manual Verification 'Phase 2: Integration with Download Flows' (Protocol in workflow.md)

## Phase 3: CLI and User Interface
- [x] Task: Update `main.py` to include the `--with-subtitles` flag. 4f23ae4
    - [x] Add `--with-subtitles` to the `argparse` configuration.
    - [x] Pass the flag value from `handle_download` to the `XiaoyuzhouDownloader`.
- [x] Task: Update `interactive_mode` in `main.py`. 4f23ae4
    - [x] Add a prompt to ask if the user wants to download subtitles.
- [x] Task: Conductor - User Manual Verification 'Phase 3: CLI and User Interface' (Protocol in workflow.md)

## Phase 4: Error Handling and Final Polish
- [x] Task: Implement graceful handling for episodes without subtitles. 4f23ae4
    - [x] Ensure the downloader skips missing subtitles without crashing the whole process.
- [x] Task: Final end-to-end verification. 4f23ae4
    - [x] Test audio + subtitle download.
    - [x] Test save-only + subtitle download.
    - [x] Test podcast-level subtitle download.
- [x] Task: Conductor - User Manual Verification 'Phase 4: Error Handling and Final Polish' (Protocol in workflow.md)
