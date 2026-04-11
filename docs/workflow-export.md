# n8n workflow export and setup notes

## Important status

The n8n workflows are not exported in this repository yet. Build and test them in your n8n instance, then export credential-free JSON files into `workflows/`. Do not invent workflow JSON or claim it is importable before validating it in n8n.

## Planned workflows

1. `Inbound Lead Processor` — Webhook and Telegram triggers, normalization, input validation, Airtable deduplication, Ollama classification, fallback, manager alert, and Google Sheets log.
2. `Daily Lead Digest` — daily schedule, Airtable `digest_pending` query, Telegram digest, status update, and Sheets log.
3. `Global Error Handler` — Error Trigger, Telegram failure alert, and Sheets failure log; assign this error workflow to the two production workflows.
4. `Classifier Evaluation` — manual trigger, ten test cases, Ollama classification, JSON validation, and accuracy summary.

## Export steps

1. Open each tested workflow in n8n.
2. Use the workflow menu to download/export the workflow JSON.
3. Confirm the export does not contain credential values, real lead data, execution payloads, private chat IDs, or production webhook URLs.
4. Save sanitized files using clear names, for example `inbound-lead-processor.json` and `daily-lead-digest.json`.
5. Keep a local copy of the original n8n credential store secure; never put credentials in Git.
6. Test each exported workflow by importing into a clean n8n instance and reconnecting credentials.

## Portability checklist

- Replace personal base/table IDs with documented setup instructions or n8n selection fields where possible.
- Replace manager chat IDs and spreadsheet IDs with clearly labeled configuration placeholders if included in an export.
- Verify the Ollama URL is `http://ollama:11434` when running in the provided Compose network.
- Ensure the Error Trigger workflow is active and selected in the settings of both operational workflows.
- Record the tested n8n version, Ollama model tag, and test date in the README after validation.
