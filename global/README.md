# Global rules (all projects)

Rules here apply to every project and every conversation, not just one. Project-specific memory stays in its own folder (`finance/`, `business/`, and the root README for the work project); do not copy these rules into those files.

## Persistent outputs go to Google Drive (set 27 Nov 2026)

- Any report, document or scan result the user wants kept (for example the Saturday SEPA screen scans) is saved to the user's Google Drive through the Google Drive connector, not only on the local machine or in a chat.
- Folder layout: `Claude Reports/<Project>/<Topic>/` in My Drive, e.g. `Claude Reports/Finance/Screen scans/`. Create the project or topic folder if it is missing.
- File names start with the date: `YYYY-MM-DD <what it is>`. Notes and reports as Google Docs; tables (CSV screen lists) as Google Sheets.
- Give the user the Drive link after saving. Local copies may still be kept, but Drive is the durable copy.
- If the Drive connector is not available in a session, say so and save locally, then upload when it is available.
