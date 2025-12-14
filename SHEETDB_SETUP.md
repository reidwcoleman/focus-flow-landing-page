# Sheet.db Setup Instructions

This landing page is configured to send waitlist submissions to Google Sheets via Sheet.db.

## Google Sheet
**Sheet URL:** https://docs.google.com/spreadsheets/d/1zETrrhGS0fcrXlGAeWvWfgxrgql_B-Two3CDrhOBdsk/edit#gid=0

**Sheet ID:** `1zETrrhGS0fcrXlGAeWvWfgxrgql_B-Two3CDrhOBdsk`

## Sheet.db Setup Steps

### 1. Visit Sheet.db
Go to [sheetdb.io](https://sheetdb.io) and create a free account.

### 2. Connect Your Google Sheet
- Click "Create Database" or "New API"
- Choose "Google Sheets"
- Paste your Google Sheets URL: `https://docs.google.com/spreadsheets/d/1zETrrhGS0fcrXlGAeWvWfgxrgql_B-Two3CDrhOBdsk/edit#gid=0`
- Grant Sheet.db access to your Google account

### 3. Verify Sheet Structure
Make sure your Google Sheet has these column headers in the first row:
- `name`
- `email`
- `timestamp`
- `source`

### 4. Get Your API ID
After connecting, Sheet.db will provide you with an API endpoint like:
```
https://sheetdb.io/api/v1/YOUR_API_ID
```

### 5. Update the Code (if needed)
The code is already configured to use the Sheet ID directly:
```javascript
const SHEETDB_API_URL = 'https://sheetdb.io/api/v1/1zETrrhGS0fcrXlGAeWvWfgxrgql_B-Two3CDrhOBdsk';
```

If Sheet.db gives you a different API ID, update line ~1729 in `index.html`.

## Data Collected

When someone joins the waitlist, the following data is sent to your Google Sheet:
- **name**: Full name entered in the form
- **email**: Email address entered in the form
- **timestamp**: ISO 8601 timestamp of submission (e.g., `2025-12-13T12:34:56.789Z`)
- **source**: Always set to "Landing Page"

## Testing

1. After setting up Sheet.db, test the form by submitting a test entry
2. Check your Google Sheet to confirm the data appears
3. The form should show a success message: "🎉 Welcome to the waitlist! Check your email for confirmation."

## Troubleshooting

### CORS Errors
If you see CORS errors in the browser console, make sure:
- Your Sheet.db account is active
- The API endpoint is correct
- The sheet is accessible to Sheet.db

### Data Not Appearing
- Check that column names in your sheet match exactly: `name`, `email`, `timestamp`, `source`
- Verify Sheet.db has permission to write to your sheet
- Check the Sheet.db dashboard for API logs

### Rate Limits
Sheet.db free tier includes:
- 10,000 API calls per month
- Unlimited sheets
- Basic support

For high traffic, consider upgrading to a paid plan.

## Alternative: Direct Google Sheets API

If you prefer not to use Sheet.db, you can use Google Sheets API directly, but this requires:
1. Google Cloud Project setup
2. OAuth 2.0 credentials
3. Service account or API key
4. More complex implementation

Sheet.db simplifies this process significantly.

## Support

- Sheet.db docs: https://docs.sheetdb.io/
- Sheet.db support: support@sheetdb.io
