# Morning AI Journals Scheduler (n8n)

This repository contains an n8n workflow that automates the discovery, reading management, and comprehension testing of daily AI & Machine Learning research papers from ArXiv.

## Features

This workflow is split into two interconnected processes:

### 1. Morning Journal Delivery (Automated)
- **Automated Scheduling:** Runs daily at 05:15 AM WIB.
- **ArXiv Integration:** Fetches the 3 latest papers in `cs.AI`, `cs.LG`, and `cs.HC`.
- **OpenAI Summarization:** Formats the papers into brief Indonesian summaries with direct links.
- **Interactive Telegram UI:** Sends the summaries to your Telegram chat along with inline buttons (`✅ Jurnal 1`, `✅ Jurnal 2`, `✅ Jurnal 3`) for each paper.

### 2. Reading Tracking & Comprehension Quiz (Interactive Callback)
- **Mark as Read:** Clicking a journal's inline button in Telegram instantly triggers a callback.
- **Google Sheets Database:** Logs the read journal into a Google Sheet with columns matching your Turso database schema (`id`, `title`, `author`, `link`, `content`, `is_read`, `created_at`, `read_count`, `source`).
- **Comprehension Quiz Generation:** Re-fetches the abstract of the selected journal from ArXiv.
- **OpenAI Quiz:** Generates a 5-question multiple-choice quiz (in Indonesian) based on the abstract to test your understanding.
- **Quiz Delivery:** Sends the 5 quiz questions back to your Telegram chat.

## How to Import
1. Download or copy the contents of [`journal-scheduler-n8n.json`](journal-scheduler-n8n.json).
2. Open your n8n dashboard.
3. Click **Add Workflow**.
4. Click the Options (⚙️) menu in the top right and select **Import from File**.
5. Select the `journal-scheduler-n8n.json` file.

## Required Credentials & Setup
Once imported, you will need to configure the following in n8n for the workflow to run properly:

1. **OpenAI API Key**: For both the `OpenAI Formatter` and `Generate Quiz` nodes.
2. **Telegram Bot Token**: For the `Send to Telegram`, `Telegram Callback Trigger`, `Answer Callback Query`, and `Send Quiz to Telegram` nodes. Make sure the Chat ID is correct.
3. **Google Sheets OAuth2**: For the `Google Sheets` node. Ensure your destination spreadsheet has row headers exactly matching:
   `id`, `title`, `author`, `link`, `content`, `is_read`, `created_at`, `read_count`, `source`.

## Customization
- **Schedule:** You can change the delivery time inside the `Schedule Trigger` node.
- **Search Query:** Modify ArXiv categories inside the `Fetch ArXiv API` nodes.
- **Quiz Difficulty:** Adjust the prompt inside the `Generate Quiz` node to make questions harder or focus on specific technical aspects.
