# AI Agent for Enterprise

An n8n AI assistant that receives requests through Telegram and can help with:

- Creating events in Google Calendar
- Sending emails through Gmail
- Retrieving Fireflies meeting titles and transcript IDs
- Fetching Fireflies meeting summaries and action items
- Responding to the user through Telegram

## Workflow overview

1. **Telegram Trigger** receives a message.
2. **AI Agent** interprets the request and selects an appropriate connected tool.
3. **Google Calendar** can create an event from the user's instructions.
4. **Gmail** can send an email using the recipient, subject, and message extracted from the request.
5. **Fireflies HTTP Request tools** query the Fireflies GraphQL API for meeting transcripts and summaries.
6. **Send a text message** returns the agent's response to Telegram.

## Files

- `ai-agent-for-enterprise.json` — workflow export for importing into n8n.

## Import and configure

1. Download `ai-agent-for-enterprise.json`.
2. In n8n, use **Import from File** to import the workflow.
3. Configure your own credentials in n8n. Credential IDs from another n8n account may not exist in your instance, so reselect or recreate credentials where required.
4. Configure the OpenAI chat model connection or select a model/provider supported by your n8n setup.
5. Configure Telegram Trigger and Telegram messaging with your own Telegram bot credentials.
6. Connect your own Gmail and Google Calendar credentials.
7. In **both** Fireflies HTTP Request tool nodes, replace the placeholder authentication with your own Fireflies API key using n8n's credential store. Do not commit real API keys to GitHub.
8. Set up the Telegram trigger/webhook as required by your n8n hosting environment.
9. Test with non-sensitive sample requests before using real email, calendar, or meeting data.

## Fireflies API key safety

The exported JSON intentionally contains the placeholder `YOUR_FIREFLIES_API_KEY` instead of a real Fireflies token. This placeholder is not a working key. For use in n8n, store your key in an n8n credential (for example, a Header Auth credential with header name `Authorization` and value `Bearer <your-key>`) and select that credential in both Fireflies HTTP Request nodes.

Never publish API keys, OAuth tokens, bot tokens, passwords, or credential exports in a public repository. If a real key was previously committed or shared, revoke it and create a replacement; deleting it from the latest file does not invalidate the old key.

## Notes and limitations

- This is a sanitized workflow export, not a turnkey hosted service. It requires credentials and setup in the importing n8n instance.
- Node availability, n8n version differences, model access, and provider API changes may require adjustments.
- The workflow can send emails and create calendar events when configured. Test carefully and only connect accounts you control.
- The exported workflow retains some original credential references and webhook/node identifiers to preserve the provided structure. These identifiers are not the same as the secret credential values, but you can reselect credentials after importing.
