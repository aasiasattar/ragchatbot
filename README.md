# 🤖 RAG Chat Bot (built with n8n)

A ready-to-use **RAG chatbot** workflow for [n8n](https://n8n.io).
You upload your business documents, and the bot answers questions using the
information inside those documents — like a smart assistant that has *read* your files.

> **RAG** = *Retrieval-Augmented Generation*. In plain words: the bot first
> **retrieves** the right piece of your document, then **generates** an answer
> based on it — so replies stay accurate instead of made-up.

---

## 📸 Preview

Here is the complete workflow as it looks inside n8n — the document-upload
pipeline on the left and the chat/AI-agent side on the right:

<p align="center">
  <img src="screenshot/Screenshot%202026-09-01%20181622.png" alt="RAG Chat Bot workflow in n8n" width="100%">
</p>

---

## ✨ What this bot does

There are **two parts** to the workflow:

1. **📤 Upload part** — You submit a document through a simple web form.
   The document is turned into "embeddings" (a searchable format) and stored
   in a **Pinecone** vector database.
2. **💬 Chat part** — When someone asks a question, an **AI Agent** searches the
   stored documents and answers using what it found. It also remembers the
   recent conversation.

---

## 🧩 What's inside the box

| Piece | What it is | Why it's here |
|-------|-----------|---------------|
| **OpenAI (GPT-4.1)** | The "brain" that writes answers | Understands questions & replies naturally |
| **OpenAI Embeddings** | Converts text into searchable numbers | Lets the bot find the right document part |
| **Pinecone** | Vector database | Stores your uploaded documents |
| **n8n AI Agent + Memory** | The workflow logic | Ties everything together, remembers chat |

---

## 🔐 Is my API key safe in this repo?

**Yes.** The workflow file (`Rag Chat Bot.json`) does **not** contain any real
passwords or API keys. n8n only exports the *names* of your credentials, never
the secret values. You add your own keys later, inside n8n. 🔒

Never commit a real `.env` file or paste your keys into the JSON — the included
`.gitignore` is set up to prevent that automatically.

---

## 🚀 How to use it (step by step)

### What you need first
- An **n8n** account or installation → https://n8n.io (free cloud trial or self-hosted)
- An **OpenAI API key** → https://platform.openai.com/api-keys
- A **Pinecone account** (free tier works) → https://app.pinecone.io

### Step 1 — Download the workflow
Download **`Rag Chat Bot.json`** from this repository
(green **Code** button → *Download ZIP*, or clone the repo).

### Step 2 — Import it into n8n
1. Open n8n.
2. Click the **⋯** menu (top-right) → **Import from File**.
3. Choose the `Rag Chat Bot.json` file. The whole workflow appears on your canvas.

### Step 3 — Add your credentials
The imported nodes will show a "credential needed" warning — that's expected.
1. **OpenAI:** click any OpenAI node → *Create New Credential* → paste your OpenAI key.
2. **Pinecone:** click a Pinecone node → *Create New Credential* → paste your Pinecone key.
3. In Pinecone, create an index named **`aasiaforge-rag`** (or change the name in
   the two Pinecone nodes to match your own index).

> 💡 Tip: use `.env.example` as a checklist of the keys you need to collect.

### Step 4 — Upload a document
1. Open the **"On form submission"** node and click its form URL (or run the workflow).
2. Upload a PDF / text file with the information you want the bot to know.

### Step 5 — Chat with it
1. Click **Open chat** at the bottom of the n8n editor.
2. Ask a question about your uploaded document — the bot answers from it. 🎉

---

## 📁 Files in this repository

| File | Purpose |
|------|---------|
| `Rag Chat Bot.json` | The n8n workflow — import this |
| `README.md` | This guide |
| `.env.example` | Checklist of the API keys you need (no real keys) |
| `.gitignore` | Keeps secrets out of the repo |
| `screenshot/` | Picture of the finished workflow |

---

## ❓ Common questions

**Do I need to know coding?**
No. Importing the file and pasting two API keys is all it takes.

**Does it cost money?**
n8n and Pinecone have free tiers. OpenAI charges a small amount per request —
usually a few cents for testing.

**Can I change what the bot answers?**
Yes — open the **AI Agent** node and edit the *System Message* to change its tone
or rules.

---

Made with ❤️ using n8n. Feel free to download, import, and reuse anytime.
