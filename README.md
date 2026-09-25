# 🤖 30-Day AI LinkedIn Post Automation

> **An n8n-powered, human-in-the-loop LinkedIn content automation workflow for creating and publishing a 30-day AI content series.**

![n8n](https://img.shields.io/badge/n8n-Workflow-EA4B71?style=for-the-badge&logo=n8n)
![AI](https://img.shields.io/badge/AI-Content%20Generation-412991?style=for-the-badge)
![LinkedIn](https://img.shields.io/badge/LinkedIn-Automation-0A66C2?style=for-the-badge&logo=linkedin)
![Gmail](https://img.shields.io/badge/Gmail-Approval-EA4335?style=for-the-badge&logo=gmail)

This project automates a **30-day LinkedIn AI content campaign** using **n8n, AI language models, Gmail, and LinkedIn**.

Every day, the workflow calculates the current campaign day, selects the corresponding AI topic, generates a LinkedIn-ready post, sends it through Gmail for a human decision, and then publishes the content to LinkedIn.

The project demonstrates a practical **AI + workflow automation + human-in-the-loop** architecture rather than a simple one-click content generator.

---

## ✨ Key Features

- 📅 **30-day AI content calendar** with predefined topics
- ⏰ **Daily scheduled execution** at 9:00 AM IST
- 🤖 **AI-generated LinkedIn posts** with a structured prompt
- 🧠 Uses an **AI Agent** with a connected chat model
- 📧 **Gmail-based approval flow**
- 🔄 **Regeneration path** for declined content
- 🔗 **Automatic LinkedIn publishing**
- 🧮 JavaScript-based **campaign day and topic calculation**
- 🛑 Automatically stops processing outside the 30-day campaign window
- 🔐 Uses n8n credentials instead of putting API secrets in the workflow logic

---

## 🏗️ Architecture

```text
┌──────────────────────────────┐
│     Schedule Trigger         │
│        9:00 AM IST           │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│     Compute Day & Topic      │
│        Day 1 → Day 30        │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│          AI Agent            │
│   Generate LinkedIn Post     │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       Gmail Approval         │
│      Review Generated Post   │
└──────────────┬───────────────┘
               │
          ┌────┴────┐
          │         │
       APPROVE    DECLINE
          │         │
          ▼         ▼
┌──────────────┐  ┌─────────────────────┐
│   LinkedIn   │  │ Regenerate Post     │
│   Publish    │  │ with another model  │
└──────────────┘  └──────────┬──────────┘
                             │
                             ▼
                    ┌─────────────────────┐
                    │ Gmail → LinkedIn   │
                    │ Regenerated version │
                    └─────────────────────┘
```

### Important workflow behavior

In the current JSON workflow:

- **Approve** → the original generated post is published to LinkedIn.
- **Decline** → the post is regenerated using the regeneration model and the regenerated version is then sent through the secondary path to LinkedIn.

If you want **decline = regenerate → ask for approval again**, add a second approval decision after `Send for Approval1` before `Post to LinkedIn1`.

---

## 🧠 30-Day AI Topic Series

| Day | Topic |
|---:|---|
| 1 | AI Agents |
| 2 | RAG |
| 3 | Embeddings |
| 4 | Vector Databases |
| 5 | Prompt Engineering |
| 6 | LLM Context Windows |
| 7 | AI Hallucinations |
| 8 | Function Calling |
| 9 | Tool Calling |
| 10 | AI Agent Memory |
| 11 | Multi-Agent Systems |
| 12 | AI Evaluation |
| 13 | Fine-Tuning |
| 14 | LoRA |
| 15 | AI APIs |
| 16 | AI Automation |
| 17 | n8n AI Agents |
| 18 | Webhooks + AI |
| 19 | AI Workflows |
| 20 | Computer Vision |
| 21 | Multimodal AI |
| 22 | AI Security |
| 23 | Prompt Injection |
| 24 | RAG Security |
| 25 | AI Cost Optimization |
| 26 | LLM Latency |
| 27 | Open-Source LLMs |
| 28 | AI Coding Assistants |
| 29 | AI in Software Development |
| 30 | The Future of Agentic AI |

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **n8n** | Workflow orchestration and automation |
| **AI Agent** | Generates structured LinkedIn content |
| **Google Gemini** | Connected chat model for the main AI Agent |
| **Claude Sonnet** | Regeneration path |
| **Gmail** | Human approval / workflow interaction |
| **LinkedIn** | Publishing generated posts |
| **JavaScript** | Campaign-day calculation and topic selection |

> **Note:** Although the workflow filenames include `(Groq)`, the inspected workflow configuration uses **Google Gemini** for the main AI Agent and **Claude Sonnet** for regeneration. Configure the credentials/models required by the JSON you choose to import.

---

## 📂 Repository Structure

```text
Linkedin-Post-Automation/
│
├── LinkedIn 30-Day AI Post Creator.json
├── LinkedIn 30-Day AI Post Creator (Groq).json
├── LinkedIn 30-Day AI Post Creator(new acc).json
└── README.md
```

The repository contains multiple workflow JSON variants. They currently share the same overall node architecture, so choose the version that matches the accounts/credentials you intend to configure.

---

# 🚀 Getting Started

## 1. Prerequisites

You need:

- An **n8n** instance (Cloud or self-hosted)
- A **Gmail account** that can be connected to n8n
- A **LinkedIn account** supported by your n8n LinkedIn integration
- Credentials for the AI model(s) used by the selected workflow
- Permission to publish content through your LinkedIn integration

---

## 2. Import the Workflow

Open your n8n editor and import one of the JSON files:

```text
LinkedIn 30-Day AI Post Creator.json
```

or one of its variants.

Typical n8n flow:

```text
n8n
 ↓
Import Workflow
 ↓
Select JSON file
 ↓
Configure credentials
 ↓
Test
 ↓
Activate
```

---

## 3. Configure AI Credentials

The workflow contains:

```text
AI Agent
   ↓
Google Gemini Chat Model
```

and a regeneration path containing:

```text
Regenerate LinkedIn Post
   ↓
Claude Sonnet 5 (Regen)
```

Connect the appropriate credentials in n8n before running the workflow.

Do not commit API keys or private credentials to GitHub.

---

## 4. Configure Gmail

The workflow uses Gmail to send the generated post for a human decision.

Find:

```text
Send for Approval
```

and configure the recipient for your own email address.

The email contains:

- Campaign day
- Topic
- Generated LinkedIn post
- Approval controls

There is also a second Gmail node:

```text
Send for Approval1
```

which is used by the regeneration branch.

---

## 5. Configure LinkedIn

Configure the LinkedIn credential used by:

```text
Post to LinkedIn
```

and:

```text
Post to LinkedIn1
```

The workflow publishes the generated text through the LinkedIn integration.

Before activating the workflow, test publishing with your own account and confirm that the integration has the required permissions.

---

# ⏰ Schedule

The workflow's schedule trigger is configured for:

```text
09:00 AM IST
```

Internally, this is represented as:

```text
03:30 UTC
```

You can change the trigger time directly in the schedule node.

---

# 📅 Campaign Day Calculation

The `Compute Day & Topic` node contains the 30-day topic array and calculates the campaign day using the configured start date:

```text
2026-09-03 → Day 1
```

The calculation effectively maps dates like:

```text
2026-09-03 → Day 1
2026-09-04 → Day 2
...
2026-10-02 → Day 30
```

Outside the 30-day window, the Code node returns no items and the workflow stops processing.

### Starting a new campaign

To reuse the workflow for another 30-day series, update:

1. The `startDate`
2. The `topics` array
3. The AI prompt if you want a different content style

The number of topics should match the intended campaign length.

---

# ✍️ AI Content Generation

The AI Agent is instructed to create a professional educational LinkedIn post containing:

- A curiosity-driven hook
- A simple explanation of the topic
- How the concept works
- Important concepts/components
- A real-world example
- Practical applications
- Key benefits
- A key takeaway
- Relevant hashtags
- Short, mobile-friendly paragraphs

The intended style is:

```text
Professional
+
Educational
+
Beginner-friendly
+
Engaging
```

The workflow prompt also asks the model to avoid unnecessary jargon and return only the LinkedIn post.

---

# 🔄 Approval & Regeneration Logic

The workflow contains an `Approved?` decision node.

### Path A — Approve

```text
Generated Post
      ↓
Gmail Approval
      ↓
Approved?
      ↓
   YES
      ↓
Post to LinkedIn
```

The original generated post is published.

### Path B — Decline

```text
Generated Post
      ↓
Gmail Approval
      ↓
Approved?
      ↓
   NO
      ↓
Regenerate LinkedIn Post
      ↓
Claude Sonnet
      ↓
Send for Approval1
      ↓
Post to LinkedIn1
```

The current workflow's decline branch **does not contain another approval decision after regeneration**. Review this behavior carefully before using it in production.

---

# 🔐 Security

Never commit secrets to this repository.

### Do not expose

```text
❌ API keys
❌ OAuth tokens
❌ Passwords
❌ Private credentials
❌ Session tokens
❌ Personal access tokens
```

Use n8n's credential management system.

Before publishing a workflow to GitHub, inspect the exported JSON and remove or replace any sensitive information.

---

# 🧪 Testing Checklist

Before activating the automation:

```text
[ ] Import workflow successfully
[ ] Configure AI credentials
[ ] Test AI content generation
[ ] Configure Gmail
[ ] Test approval email
[ ] Configure LinkedIn
[ ] Test LinkedIn publishing
[ ] Verify campaign start date
[ ] Verify topic list
[ ] Verify schedule and timezone
[ ] Review decline/regeneration behavior
[ ] Activate workflow
```

For production use, first run a complete test with a non-critical LinkedIn post.

---

# 🧩 Main n8n Nodes

| Node | Responsibility |
|---|---|
| **Daily 9 AM IST** | Starts the workflow daily |
| **Compute Day & Topic** | Calculates campaign day and selects topic |
| **AI Agent** | Generates the LinkedIn post |
| **Google Gemini Chat Model** | Provides the main AI model |
| **Send for Approval** | Sends content to Gmail |
| **Approved?** | Determines the approval path |
| **Post to LinkedIn** | Publishes the approved original post |
| **Regenerate LinkedIn Post** | Creates an alternative post |
| **Claude Sonnet 5 (Regen)** | Model used for regeneration |
| **Send for Approval1** | Handles the regenerated-post branch |
| **Post to LinkedIn1** | Publishes the regenerated post |

---

# 💡 Why This Project Matters

This project demonstrates more than AI text generation.

It combines several real-world automation concepts:

```text
Scheduling
    +
AI Content Generation
    +
Prompt Engineering
    +
Human-in-the-Loop
    +
Conditional Logic
    +
Content Regeneration
    +
Social Media Automation
```

It is a practical example of how AI can be integrated into an automated business workflow while keeping a human involved in the content pipeline.

---

# 🔮 Possible Improvements

Ideas for extending the project:

- [ ] Add a second approval step after regeneration
- [ ] Store published posts in Google Sheets, Airtable, or a database
- [ ] Add duplicate-content detection
- [ ] Add LinkedIn analytics collection
- [ ] Track likes, comments, impressions, and engagement rate
- [ ] Add automatic failure notifications
- [ ] Add retry handling for failed API calls
- [ ] Add content-quality scoring before approval
- [ ] Generate post images automatically
- [ ] Support multiple LinkedIn accounts
- [ ] Allow custom topic lists from a spreadsheet
- [ ] Add campaign pause/resume controls
- [ ] Add an approval dashboard
- [ ] Add observability and execution logging

---

# 🎯 Use Cases

This automation can be adapted for:

- 👨‍💻 Personal AI/tech branding
- 📚 Educational content series
- 🏢 Company LinkedIn content
- 🚀 Startup content marketing
- 🧑‍💼 Professional thought leadership
- 📰 Technology newsletters and campaigns
- 📈 Social media content workflows

---

# 📌 Project Highlights

**Problem:** Creating consistent, educational LinkedIn content every day requires planning, writing, formatting, and publishing time.

**Solution:** Automate the repetitive parts with n8n and AI while keeping a human in the publishing workflow.

**Result:** A reusable 30-day content pipeline that connects scheduling, AI generation, approval, regeneration, and LinkedIn publishing.

---

## 👨‍💻 Author

**Sri Vardhan Jilla**

B.Tech Computer Science Engineering | AI & GenAI Enthusiast

- GitHub: [@jillasrivardhan](https://github.com/jillasrivardhan)
- LinkedIn: [Jilla Srivardhan](https://www.linkedin.com/in/jilla-srivardhan)

---

## ⭐ Support

If you find this workflow useful, consider giving the repository a ⭐ and sharing your improvements.

---

## 📄 License

No license file is currently included in the repository.

If you plan to make the workflow publicly reusable, consider adding an appropriate open-source license.
