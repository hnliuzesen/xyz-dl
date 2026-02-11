# Product Guidelines - xyz-dl

## Voice and Tone
- **Professional and Concise:** The tool should communicate with the user in a direct, objective, and minimalist manner. Avoid unnecessary conversational filler.
- **Clarity Over Verbosity:** Prioritize clear, unambiguous messages. For automation, output should be predictable and easy to parse.

## Documentation and Text
- **Bilingual Context:** While the primary documentation and CLI interface should follow professional standards (likely English), the tool must handle and display Chinese characters (UTF-8) correctly, as most podcast metadata will be in Chinese.
- **Self-Documenting CLI:** Commands and options should have clear, concise descriptions available via `--help`.

## Visual Identity (CLI)
- **Standardized Output:** Use consistent formatting for tables, lists, and progress bars.
- **Color Usage:** Use ANSI colors sparingly to highlight important information (e.g., green for success, red for errors) without cluttering the terminal.

## Quality Standards
- **Error Handling:** Provide actionable error messages. If a download fails, explain why and, if possible, how the user can fix it.
- **Predictability:** The tool should behave consistently across different operating systems and terminal environments.
