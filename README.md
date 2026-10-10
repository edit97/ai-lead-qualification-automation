# AI Lead Qualification & Sales Automation (n8n)

An AI-assisted sales lead processing workflow built in n8n. Portfolio demo with Google Sheets CRM, Telegram approval, Gmail and OpenAI.

## Features
- Receives leads via a POST webhook and validates required fields
- Normalizes input and checks Google Sheets for duplicate emails
- Uses an LLM to classify intent, urgency, requirements clarity and complexity
- Calculates a deterministic 0–100 lead score and routes HOT/WARM/COLD leads
- Saves HOT leads to Google Sheets and notifies a Telegram chat
- Generates a personalized email draft, saved to the CRM
- Requires explicit Telegram Approve/Reject before Gmail sends the email
- Updates the CRM status to SENT or REJECTED and confirms in Telegram
- Sends Telegram notifications for invalid and duplicate leads

**Current scope:** The HOT lead path and approval/rejection workflow are configured. WARM/COLD processing, follow-up scheduling and centralized error handling are planned enhancements. This export is a configuration snapshot, not a live hosted demo.

## Workflow setup
1. Import `workflow.json` into an n8n instance.
2. Reconnect your own OpenAI, Google Sheets, Gmail and Telegram credentials.
3. Replace `YOUR_GOOGLE_SHEET_ID` with the ID of your own CRM spreadsheet; create a `Leads` sheet with columns matching the node mappings.
4. Replace `YOUR_TELEGRAM_CHAT_ID` in Telegram notification/approval nodes.
5. Review webhook URLs and configure Telegram callback delivery before enabling the workflow.
6. Test using addresses and accounts you own. Approval can send real emails.

## Example lead payload
```json
{
  "name": "Demo Lead",
  "email": "your-test-address@example.com",
  "company": "Example Co",
  "website": "https://example.com",
  "message": "We need an AI sales automation workflow integrated with our CRM.",
  "budget": 3500,
  "deadline": "3 weeks",
  "source": "website"
}
```

## Notes
- No credentials are included in the public export.
- Configure your own services before running; the workflow will not work out of the box.
- Never publish API keys, OAuth tokens, customer data or execution logs.
