# Morning AI Journals Scheduler (n8n)

This repository contains an n8n workflow that automatically fetches the latest AI & Machine Learning research papers from ArXiv every morning, summarizes them using OpenAI, and sends them to Telegram.

## Features
- **Automated Scheduling:** Runs daily at 05:15 AM WIB.
- **ArXiv Integration:** Fetches latest papers in `cs.AI`, `cs.LG`, and `cs.HC`.
- **OpenAI Summarization:** Formats the papers into brief Indonesian summaries with direct links.
- **Telegram Notifications:** Sends the summary directly to your Telegram chat.

## How to Import
1. Download or copy the contents of [`journal-scheduler-n8n.json`](journal-scheduler-n8n.json).
2. Open your n8n dashboard.
3. Click **Add Workflow**.
4. Click the Options (⚙️) menu in the top right and select **Import from File**.
5. Select the `journal-scheduler-n8n.json` file.

## Required Credentials
Once imported, you will need to configure the following credentials in n8n for the workflow to run properly:

1. **OpenAI API Key**: For the `OpenAI Formatter` node.
2. **Telegram Bot Token**: For the `Send to Telegram` node. Make sure the Chat ID is correct.

## Customization
- **Schedule:** You can change the run time by clicking the `Schedule Trigger` node.
- **Search Query:** You can modify the ArXiv categories inside the `Fetch ArXiv API` node.
- **Prompt:** You can tweak the AI prompt inside the `OpenAI Formatter` node to adjust the summary style.
