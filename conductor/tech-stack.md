# Technology Stack - xyz-dl

## Core Technologies
- **Python:** Version >= 3.13. Chosen for its robust library support and suitability for CLI tools.
- **uv:** A fast Python package installer and resolver. Used for managing project dependencies and environments.

## External Dependencies
- **requests:** Used for making HTTP requests to the Xiaoyuzhou FM API.
- **tqdm:** Used for providing real-time, visual progress bars for downloads in the terminal.

## Architecture
- **Modular CLI:** The project is structured into functional modules (e.g., `api.py`, `auth.py`, `downloader.py`) to ensure maintainability and ease of extension.
