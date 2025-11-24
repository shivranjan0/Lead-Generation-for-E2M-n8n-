# Lead Gen for E2M – n8n Workflow

A comprehensive automation workflow to generate, analyze, and organize leads using **n8n**, **Apify**, **OpenAI**, and **Google Sheets**.

This workflow automates the process of scraping businesses from Google Maps based on user input, analyzing their websites using AI to generate "Pain Points" and "Recommended Services," and drafting cold emails.

---

## 🛠 Prerequisites

Before running this workflow, ensure you have the following:

- **n8n Instance:** Cloud or Self-hosted version.
- **Apify Account:** With an active API Token.
- **OpenAI Account:** With a valid API Key (GPT-3.5 or GPT-4).
- **Google Cloud Project:** With Google Sheets API enabled (for OAuth2).
- **The Workflow JSON File:** The code to import into n8n.

---

## 🚀 Setup Instructions

### Step 1: Import Workflow

1. Open your **n8n dashboard**.
2. Navigate to **Workflows** > **Import from Clipboard/File**.
3. Paste your provided JSON workflow code or upload the file.
4. Click **Save**.

### Step 2: Configure Credentials

You must configure three main services for the nodes to function correctly.

#### 🔹 2.1 Google Sheets OAuth2

1. In n8n, go to **Credentials** > **Create New**.

# Lead-Generation-for-E2M — n8n Workflow

A concise n8n workflow to find businesses on Google Maps, analyze their websites with AI, generate pain points & recommended services, and draft personalized cold emails.

---

## 🧭 Quick Overview

- **Tools used:** n8n, Apify (Google Maps scraper), OpenAI (LLM), Google Sheets.
- **Purpose:** Automate lead discovery and generate outreach content.

---

## 🛠 Prerequisites

- `n8n` (cloud or self-hosted)
- Apify account (API token)
- OpenAI account (API key)
- Google Cloud project with Google Sheets API enabled
- The workflow JSON file: `lead gen for e2m (1).json`

---

## 🚀 Setup Instructions

### 1) Import the workflow

1. Open your n8n dashboard.
2. Go to **Workflows → Import from Clipboard/File**.
3. Upload `lead gen for e2m (1).json` or paste its contents.
4. Save the workflow.

### 2) Configure credentials

- **Google Sheets (OAuth2):** Create a credential and attach it to the `final lead generated`, `companies which dont have a website`, and `error log` nodes.
- **OpenAI:** Create an OpenAI credential (API key starting with `sk-...`) and attach it to `summarizing website and suggestion services`.
- **Apify:** For the `apify google map scraper` node, replace the placeholder token with your Apify API token locally. Do NOT commit your token to the repo — use environment variables or n8n credentials.

---

## 📄 Google Sheet setup

Create a Google Sheet with exactly 3 tabs. The names and headers must match the workflow mappings.

- **Tab name:** `leads` — headers (first row):
  - `title`, `address`, `city`, `state`, `countryCode`, `website`, `phoneUnformatted`, `domain`, `company_summary`, `Pain_Points`, `Recommended_E2M_Solutions_Services`, `cold_email_html`
- **Tab name:** `companies which dont have a website` — headers: use whatever the workflow expects (the tab is referenced by gid in the workflow).
- **Tab name:** `error log` — headers: whatever the workflow expects for logging errors.

---

## 🔒 Security notes

- Remove any hard-coded API tokens from files. Use n8n credentials or environment variables.
- If a secret was ever committed, rotate/revoke it (treat as compromised).
- Consider adding `.env.example` and `.gitignore`, and enable a pre-commit secret scanner.

---

## ▶️ Run / Test

1. Import the workflow and configure credentials.
2. Trigger the workflow via the form trigger in n8n or run it manually.

---

## ❓ Troubleshooting

- If pushes to GitHub are blocked, check GitHub secret-scanning alerts and remove secrets from commits (amend/rebase) before pushing.
- If the workflow fails in n8n, inspect the node error output and check credentials.

---

## Contributing

PRs welcome — keep secrets out of commits and follow the security notes above.

---

## License

See the repository settings for licensing information.
