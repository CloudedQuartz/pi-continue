Format the supplied `<continuation-ledger>` into the strict `pi-continue-artifacts/v3` JSON object requested by the system prompt.

Rules:

- Preserve only facts present in the ledger and runtime sections.
- Keep exact paths, commands, identifiers, user constraints, validation status, and recency resolution when present.
- Do not invent missing progress, validation, file contents, user approvals, durable-document writes, or guide writes.
- Use empty arrays for absent optional array fields, but never leave `recencyLedger` empty.
- If no durable promotion exists, emit one `durablePromotions` entry with status `none` and concise explanatory strings for the other required fields.
- Set `document` equal to `brief` unless durable document-specific content is clear.
- Set `agentGuideMarkdown` to null unless a full guide replacement is explicitly supplied.
- Set `agentGuideChangeReason` to a short non-empty explanation of the guide decision.
- Return only JSON.
