# Telegram AI Search Agent 🤖🔍

An autonomous, multi-turn AI conversational agent built with [n8n](https://n8n.io/) that connects **Telegram** to an LLM reasoning engine backed by real-time web search capabilities.

---

## 📌 Overview

This workflow transforms a standard Telegram bot into an intelligent AI assistant. Rather than relying solely on static training data, the agent dynamically determines when external information is needed, searches the live web via SerpApi (Google Search), maintains conversational context across messages, and sends structured responses directly back to the user.

---

## 🏗️ Architecture & Workflow

The workflow consists of three main stages:

1. **Trigger & Ingestion:**
   * **Telegram Trigger (`Updates: message`):** Listens for incoming messages sent to your Telegram Bot via webhooks.

2. **AI Reasoning Engine (`AI Agent`):**
   * **Model Provider:** OpenAI Chat Model (handles natural language understanding, reasoning, and response generation).
   * **Memory:** Window Buffer Chat Memory (tracks session context and chat history to enable multi-turn dialogue).
   * **Tools:** `google_search` via SerpApi (allows the agent to execute real-time web searches when answering recent or factual queries).

3. **Response Dispatch:**
   * **Send Reply (`sendMessage: message`):** Routes the finalized AI response back to the corresponding Telegram Chat ID.

---

## 🚀 Key Features

* **Autonomous Tool Use:** The agent decides whether to answer from internal knowledge or trigger a Google search.
* **Context Retention:** Keeps track of previous messages so users can ask follow-up questions naturally.
* **Low-Latency Webhook Pipeline:** Real-time event handling using n8n's workflow orchestration.
* **Modular Integration:** Easy to swap the LLM (e.g., Anthropic, Gemini, Ollama) or add additional tools (e.g., databases, calculators, custom APIs).

---

## 🛠️ Prerequisites

Before running the workflow, make sure you have:

* An active **n8n** instance (Cloud or self-hosted).
* A **Telegram Bot Token** (generated via [@BotFather](https://t.me/BotFather)).
* An **OpenAI API Key** (or compatible LLM provider credentials).
* A **SerpApi Key** (for Google Search tool integration).

---

## ⚙️ Setup & Installation

1. **Clone or Export Workflow:**
   * In your n8n canvas, click the three dots (`...`) in the top navigation bar and select **Export**.
   * Save the JSON file into your GitHub repository as `workflow.json`.

2. **Configure Credentials in n8n:**
   * **Telegram API:** Paste your Bot Token obtained from BotFather.
   * **OpenAI API:** Add your OpenAI secret key under OpenAI credentials.
   * **SerpApi:** Add your SerpApi API key to authenticate Google Search queries.

3. **Import to n8n:**
   * Go to **Workflows** > **Import from File / URL** and select `workflow.json`.
   * Attach your configured credentials to the respective nodes.

4. **Activate the Agent:**
   * Toggle the workflow status from **Inactive** to **Published / Active**.
   * Open your Telegram bot and send a message to start interacting!

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
