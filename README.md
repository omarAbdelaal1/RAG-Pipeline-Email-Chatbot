<div align="center">

# 🤖 End-to-End RAG Pipeline & Email Chatbot (n8n Workflow)

[![n8n.io](https://img.shields.io/badge/n8n-Workflow-FF6C37?logo=n8n&logoColor=white)](https://n8n.io/)
[![OpenAI](https://img.shields.io/badge/OpenAI-Embeddings-412991?logo=openai&logoColor=white)](https://openai.com/)
[![Pinecone](https://img.shields.io/badge/Pinecone-Vector_Store-000000?logoColor=white)](https://www.pinecone.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**An intelligent, autonomous n8n workflow that monitors a Gmail inbox for support queries, utilizes Pinecone RAG for factual answers, drafts friendly AI responses via GPT-4o-mini, and automatically replies to the customer while categorizing the thread.**

</div>

---

## 📑 Table of Contents
- [About the Workflow](#-about-the-workflow)
- [Architecture & Flow](#-architecture--flow)
- [Key Features](#-key-features)
- [Security Note](#-security-note)
- [Installation & Setup](#-installation--setup)
- [Required Credentials](#-required-credentials)
- [Contact](#-contact)

---

## 📖 About the Workflow

This repository contains the `RAG Pipeline and Chatbot.json` exported blueprint for an advanced [n8n](https://n8n.io/) workflow. This automation acts as a comprehensive "Closed-Loop" AI Support Agent for the fictional company "Deep-X." 

It builds upon standard AI filtering by not just generating the response, but actually executing the resolution: replying directly via Gmail APIs and applying organizational labels—resulting in a genuine "Level-1 Support" replacement.

---

## 🏗️ Architecture & Flow

The logic processes inbound communications through 6 critical phases:

1. **Trigger Phase**: Monitors the connected Gmail inbox every 1 minute.
2. **Triage Phase**: A LangChain Text Classifier evaluates the email body. If it is generic (`Other`), it halts at a `NoOp` to conserve API tokens.
3. **Reasoning Phase (AI Agent)**: LangChain interfaces with OpenRouter's `gpt-4o-mini` model, instructed to act as "Mr.X", responding with a friendly, emoji-rich tone.
4. **Knowledge Retrieval (RAG)**: The AI automatically searches an embedded Pinecone Vector database containing company FAQs/Policies to ground its answers in factual reality.
5. **Action: Reply**: The drafted AI response is piped back into a Gmail node to instantly reply to the sender's original thread.
6. **Action: Organization**: A final Gmail node categorizes the handled thread with a specific label (e.g., `CATEGORY_SOCIAL`) to keep the human inbox clean.

---

## ✨ Key Features

- **"Closed-Loop" Execution**: Goes beyond drafting templates. It actively manages the conversation lifecycle by sending the emails and organizing the inbox.
- **Retrieval Augmented Generation (RAG)**: Connects OpenAI embeddings with Pinecone to eliminate LLM hallucinations on policy questions.
- **Intelligent Routing**: Ignores spam or unrelated threads using text classification, saving computing costs.
- **Branded Persona**: The AI strictly adheres to the "Deep-X" brand voice.

---

## 🔒 Security Note

This exported `.json` blueprint is **100% credential-free and safe to distribute**. 

n8n intentionally strips out your real API keys, passwords, and OAuth tokens upon export, replacing them with generic internal tracking IDs (e.g., `"id": "b4xYFN6ucsdJYyhx"`). You can fork or download this node tree without compromising your developer accounts.

---

## 🚀 Installation & Setup

1. **Self-Hosted or Cloud n8n**: Ensure you have a running instance of n8n.
2. **Import Workflow**:
   - Navigate to your n8n dashboard.
   - Click **Add Workflow** -> **Import from File...**
   - Upload the `RAG Pipeline and Chatbot.json` file.
3. **Configure Nodes**: The blueprint will import safely, but the nodes will require your personal API keys to activate (see below).

---

## 🔑 Required Credentials

To bring this AI Agent online, link the following credentials inside your n8n instance:

- **Gmail OAuth2**: Required for the trigger, the reply node, and the labeler node.
- **OpenRouter API**: Required for the LangChain Chat Models to access `gpt-4o-mini`.
- **Pinecone API**: Required to link your specific Pinecone Index/Environment for FAQ retrieval.
- **OpenAI API**: Required for the `Embeddings OpenAI` node to vectorize search queries.

---

## 📬 Contact

**Omar Abdelaal** - [oabdelall2004@gmail.com](mailto:oabdelall2004@gmail.com)

Project Link: [https://github.com/omarAbdelaal1/End-to-End-RAG-Pipeline-Chatbot](https://github.com/omarAbdelaal1/End-to-End-RAG-Pipeline-Chatbot)
