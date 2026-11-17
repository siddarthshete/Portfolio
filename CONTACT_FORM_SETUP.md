# Contact Form Excel Workflow Setup Guide

I've updated the contact form to use an **Excel/Google Sheets workflow**. This allows form submissions to be directly saved to a spreadsheet with the date and time of submission.

## Recommended: SheetDB (Easiest Integration)

[SheetDB](https://sheetdb.io/) is a service that turns any Google Sheet into a JSON API.

### Setup Steps:

1.  **Create a Google Sheet:**
    -   Create a new Google Sheet.
    -   In the first row (headers), add the following column names:
        `name`, `email`, `subject`, `message`, `date`, `time`, `timestamp`
    -   Give your sheet a name.

2.  **Get SheetDB API URL:**
    -   Go to [sheetdb.io](https://sheetdb.io/) and log in (you can use Google).
    -   Click "Create New API".
    -   Paste the link to your Google Sheet.
    -   Copy the generated API URL (e.g., `https://sheetdb.io/api/v1/58f61be4edb3c`).

3.  **Update the Code:**
    -   Open `index.html`.
    -   Find the line: `const SHEETDB_API_URL = 'YOUR_SHEETDB_API_URL';`
    -   Replace `'YOUR_SHEETDB_API_URL'` with your actual API URL.

4.  **Test the Form:**
    -   Open your portfolio in a browser.
    -   Fill out the contact form and click "Send Message".
    -   Check your Google Sheet; the new data should appear instantly with the date and time.

## Why this workflow?

-   **No Backend Required:** You don't need to host a separate Node.js server.
-   **Data Persistence:** All messages are organized in a spreadsheet for easy tracking.
-   **Automated Timestamp:** The code automatically adds the current date and time to every entry.
-   **Free Tier:** SheetDB offers a generous free tier for personal use.

## Alternative: Google Apps Script (Fully Free)

If you prefer a completely free solution without using a third-party service like SheetDB, you can use Google Apps Script as a web hook.

1.  In your Google Sheet, go to **Extensions > Apps Script**.
2.  Paste a script that handles `doPost(e)` and appends data to the sheet.
3.  Deploy it as a **Web App** with access set to "Anyone" (even anonymous).
4.  Use the deployment URL as your `SHEETDB_API_URL` (the code might need slight adjustments for the payload structure).
