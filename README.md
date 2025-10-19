# Receipt and Expenses Tracker Automation

This project demonstrates an **n8n workflow** for automating receipt and expenses tracking. It integrates **Telegram**, **Google Sheets**, **Google Drive**, and **Google Gemini AI** to process and store expense data efficiently. This project is designed to showcase automation capabilities.

---

## Features

1. **Telegram Integration**:
   - Acts as the trigger for the workflow.
   - Supports two commands:
     - `/manual`: Allows users to manually input a description and cost.
     - `/picture`: Allows users to upload a receipt image.

2. **AI-Powered Text Extraction**:
   - Receipt images are sent to an AI Agent Node using the **Google Gemini API**.
   - Extracts and processes text from the receipt image.
   - Identifies key fields such as merchant name, subtotal, tax, total, and more.

3. **Revision Support**:
   - If the user finds inaccuracies in the extracted data, they can request a revision.
   - The workflow caters to revisions until the user is satisfied.

4. **Data Storage**:
   - Extracted data is stored in **Google Sheets** with predefined headers.
   - Receipt images are uploaded to a designated folder in **Google Drive**.

---

## Setup Instructions

### Prerequisites

1. **Telegram Bot**:
   - Create a Telegram bot and obtain the bot token.
   - Set up the following commands:
     - `/picture`
     - `/manual`

2. **Google Drive and Sheets**:
   - Create a Google Cloud Project.
   - Enable the **Google Sheets API**.
   - Create a **Service Account** for Google Sheets and obtain the email and private key.
   - Create an **OAuth 2.0 Client** for Google Drive and obtain the client ID and secret.
   - Add the service account as an editor to the Google Sheet.
   - Set up the following headers in the Google Sheet:
     - `RECORD_ID`, `TYPE`, `DESCRIPTION`, `TOTAL COST`, `TOTAL W/O TAX`, `TAX`, `DATETIME LOGGED`, `MONTH - YEAR`, `DETAILED DESCRIPTION`, `RECEIPT URL`.

3. **Google Gemini Chat Node**:
   - Go to **Google AI Studio**.
   - Create an API key for the Gemini API.

---

## Workflow Overview

1. **Trigger**:
   - The workflow starts when a user sends a command (`/manual` or `/picture`) to the Telegram bot.

2. **Manual Input**:
   - For `/manual`, the user provides a description and cost, which are directly processed and stored.

3. **Image Processing**:
   - For `/picture`, the user uploads a receipt image.
   - The image is sent to the AI Agent Node, which uses the Google Gemini API to extract text.
   - The extracted text is processed to identify key fields.

4. **Revision Handling**:
   - If the user requests a revision, the workflow allows them to edit the extracted data.

5. **Data Storage**:
   - Once the user is satisfied, the extracted data is appended to a Google Sheet.
   - The receipt image is uploaded to a designated folder in Google Drive.

---

## Example Workflow in Action

### /manual
![Manuel workflow](./samples/manual.gif)

### /picture
![Picture workflow](./samples/picture.gif)

---

## File Structure

```
receipt-automation/
├── docker/
│   ├── docker-compose.yml
│   ├── .env
├── workflow/
│   └── expenses-tracker.json
├── samples/
│   └── ...
└── README.md
```

---

## Future Enhancements

- Edit from Sheets
- Add support for additional storage options (e.g., Dropbox, OneDrive).

---

## License

This project is open-source and available under the [MIT License](LICENSE).

---

## Author

Created by Emmanuel Pedroza.

For more projects, visit my [GitHub Portfolio](https://github.com/mand0ng).
