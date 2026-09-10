# 🤖 30-Day AI LinkedIn Post Automation with n8n

An automated **30-Day AI LinkedIn Content Creator** built with **n8n, OpenAI, Gmail, and LinkedIn**.

This workflow automatically generates one AI-focused LinkedIn post every day for 30 days. Before anything is published, the generated post is sent to your Gmail account for **manual approval**. If you approve it, n8n automatically publishes the post to LinkedIn.

The goal of this project is to demonstrate how **AI + workflow automation + human approval** can be combined to create a practical content automation system.

---

## ✨ What This Automation Does

The workflow automatically:

1. Runs every day at **9:00 AM IST**
2. Determines the current day of the 30-day campaign
3. Selects the corresponding AI topic
4. Uses OpenAI to generate a LinkedIn post
5. Sends the generated post to Gmail for approval
6. Waits for your decision
7. Publishes the post to LinkedIn if approved
8. Skips publishing if declined
9. Automatically stops after Day 30

---

## 🧠 30-Day AI Content Series

The workflow contains a predefined 30-day AI topic sequence:

| Day | Topic                      |
| --: | -------------------------- |
|   1 | AI Agents                  |
|   2 | RAG                        |
|   3 | Embeddings                 |
|   4 | Vector Databases           |
|   5 | Prompt Engineering         |
|   6 | LLM Context Windows        |
|   7 | AI Hallucinations          |
|   8 | Function Calling           |
|   9 | Tool Calling               |
|  10 | AI Agent Memory            |
|  11 | Multi-Agent Systems        |
|  12 | AI Evaluation              |
|  13 | Fine-Tuning                |
|  14 | LoRA                       |
|  15 | AI APIs                    |
|  16 | AI Automation              |
|  17 | n8n AI Agents              |
|  18 | Webhooks + AI              |
|  19 | AI Workflows               |
|  20 | Computer Vision            |
|  21 | Multimodal AI              |
|  22 | AI Security                |
|  23 | Prompt Injection           |
|  24 | RAG Security               |
|  25 | AI Cost Optimization       |
|  26 | LLM Latency                |
|  27 | Open-Source LLMs           |
|  28 | AI Coding Assistants       |
|  29 | AI in Software Development |
|  30 | The Future of Agentic AI   |

---

# 🔄 How the Automation Works

```text
                    ┌──────────────────────┐
                    │   Schedule Trigger   │
                    │      9 AM IST        │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Compute Day & Topic  │
                    │ Determine Day 1-30   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Generate LinkedIn    │
                    │ Post using OpenAI    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Gmail Approval    │
                    │  Review the content  │
                    └──────────┬───────────┘
                               │
                       ┌───────┴───────┐
                       │               │
                    APPROVE          DECLINE
                       │               │
                       ▼               ▼
              ┌────────────────┐  ┌─────────────┐
              │ Post to        │  │ Post Skipped│
              │ LinkedIn       │  │             │
              └────────────────┘  └─────────────┘
```

---

# 🛠️ Technologies Used

* **n8n** — Workflow automation
* **OpenAI** — AI-powered LinkedIn content generation
* **Gmail** — Human approval system
* **LinkedIn** — Automatic publishing
* **JavaScript** — Day calculation and topic selection

---

# 📂 Repository Structure

```text
Linkedin-Post-Automation/
│
├── LinkedIn 30-Day AI Post Creator.json
│
└── README.md
```

The main file is:

```text
LinkedIn 30-Day AI Post Creator.json
```

This is the n8n workflow that you can import directly into your n8n instance.

---

# 🚀 How to Use This Automation

## Step 1 — Install / Open n8n

You need an n8n instance.

You can use:

* n8n Cloud
* Self-hosted n8n
* Local n8n installation

Open your n8n editor.

---

# Step 2 — Import the JSON Workflow

Download or clone this repository.

Inside the repository, you will find:

```text
LinkedIn 30-Day AI Post Creator.json
```

In n8n:

```text
Open n8n
   ↓
Create / Open a workflow
   ↓
Import from File
   ↓
Select:
LinkedIn 30-Day AI Post Creator.json
```

After importing, you should see the complete workflow.

The workflow contains these nodes:

```text
Daily 9 AM IST
       ↓
Compute Day & Topic
       ↓
Generate LinkedIn Post
       ↓
Send for Approval
       ↓
Approved?
     ↙     ↘
   YES      NO
    ↓        ↓
LinkedIn   Post Skipped
```

---

# 🔐 Step 3 — Connect Your OpenAI Account

The workflow uses OpenAI to generate the LinkedIn content.

Open:

```text
Generate LinkedIn Post
```

Then configure the OpenAI credentials in n8n.

You need an OpenAI API credential with access to the model used by the workflow.

The AI is instructed to create posts that:

* Are approximately 150–300 words
* Start with an engaging hook
* Explain the AI topic
* Provide practical insights
* Use short paragraphs
* End with a question
* Include 3–5 relevant hashtags
* Maintain a professional and conversational tone

---

# 📧 Step 4 — Connect Your Gmail Account

The workflow uses Gmail as a **human approval step**.

Open:

```text
Send for Approval
```

Connect your Gmail account through n8n.

The workflow sends the generated post to the configured email address.

You should change the recipient email to **your own Gmail address**.

For example:

```text
your-email@gmail.com
```

Do not use the repository author's email address unless you intentionally want the workflow to send approvals there.

---

# ✅ Step 5 — Approve or Decline the Post

Every day, the automation generates a LinkedIn post.

You will receive an email containing something similar to:

```text
Day 1 of 30 — AI Agents

Here is today's AI-generated LinkedIn post.

[Generated LinkedIn Content]

Approve & Post
Decline
```

You can review the content before it reaches LinkedIn.

### If you click Approve

```text
Gmail
  ↓
Approved?
  ↓
YES
  ↓
LinkedIn
  ↓
Post Published
```

### If you click Decline

```text
Gmail
  ↓
Approved?
  ↓
NO
  ↓
Post Skipped
```

This gives you **human control over every post**.

---

# 💼 Step 6 — Connect Your LinkedIn Account

The workflow contains a:

```text
Post to LinkedIn
```

node.

Connect your LinkedIn credentials through n8n.

The LinkedIn node is responsible for publishing the generated content.

The workflow is configured to publish with:

```text
Visibility: PUBLIC
```

Make sure your LinkedIn account has the permissions required by the LinkedIn integration available in your n8n environment.

---

# ⏰ Step 7 — Understand the Schedule

The workflow is configured to run every day at:

```text
9:00 AM IST
```

The schedule is represented internally as:

```text
03:30 UTC
```

because India Standard Time is UTC+5:30.

You can change the schedule inside:

```text
Daily 9 AM IST
```

if you want the automation to run at a different time.

---

# 📅 Step 8 — How the 30-Day Counter Works

The workflow has a predefined campaign start date:

```text
2026-09-03
```

The JavaScript node calculates how many days have passed since the campaign started.

For example:

```text
2026-09-03 → Day 1
2026-09-04 → Day 2
2026-09-05 → Day 3
...
2026-10-02 → Day 30
```

The workflow then selects the corresponding topic from the topic list.

For example:

```javascript
const topic = topics[dayNumber - 1];
```

If the current date is outside the 30-day campaign:

```text
Day < 1
OR
Day > 30
```

the workflow stops processing.

---

# 🧩 Understanding Each n8n Node

## 1. Daily 9 AM IST

**Node Type:**

```text
Schedule Trigger
```

Purpose:

Starts the workflow automatically every day at 9:00 AM IST.

---

## 2. Compute Day & Topic

**Node Type:**

```text
Code
```

Purpose:

Calculates:

```text
Current campaign day
+
Today's AI topic
```

It returns data similar to:

```json
{
  "dayNumber": 1,
  "topic": "AI Agents"
}
```

---

## 3. Generate LinkedIn Post

**Node Type:**

```text
OpenAI
```

Purpose:

Uses AI to turn the selected topic into a LinkedIn-ready post.

The AI receives:

```text
Topic
+
Day number
+
30-day series context
```

and generates the content.

---

## 4. Send for Approval

**Node Type:**

```text
Gmail
```

Purpose:

Sends the generated post to your Gmail account.

This is an important part of the workflow because the AI does **not immediately publish** the content.

You get the opportunity to review it first.

---

## 5. Approved?

**Node Type:**

```text
IF
```

Purpose:

Checks your Gmail approval response.

There are two possible paths:

```text
Approved = TRUE
```

or

```text
Approved = FALSE
```

---

## 6. Post to LinkedIn

**Node Type:**

```text
LinkedIn
```

Purpose:

Publishes the approved post to LinkedIn.

The generated AI content is passed directly into the LinkedIn publishing node.

---

## 7. Post Skipped

**Node Type:**

```text
No Operation
```

Purpose:

Handles the declined approval path.

If you decline the post, nothing is published.

---

# 🔑 Credentials You Need

Before activating the workflow, configure these integrations in n8n:

| Service  | Why it is required     |
| -------- | ---------------------- |
| OpenAI   | Generate AI content    |
| Gmail    | Send approval email    |
| LinkedIn | Publish approved posts |

You should connect **your own accounts**.

Never put API keys, passwords, OAuth tokens, or other credentials directly inside the workflow JSON or GitHub repository.

---

# ⚠️ Important Security Note

This repository contains the **workflow structure**, not your personal credentials.

Before sharing your workflow publicly:

```text
❌ Do not commit API keys
❌ Do not commit passwords
❌ Do not expose OAuth tokens
❌ Do not expose private credentials
❌ Do not hard-code sensitive information
```

Use n8n's credential system instead.

---

# 🧪 How to Test the Workflow

Before activating the automation for 30 days, test it manually.

Recommended testing process:

```text
1. Import the JSON
        ↓
2. Configure OpenAI
        ↓
3. Configure Gmail
        ↓
4. Configure LinkedIn
        ↓
5. Test the OpenAI node
        ↓
6. Test Gmail approval
        ↓
7. Approve the test post
        ↓
8. Verify LinkedIn publishing
        ↓
9. Activate the workflow
```

Always verify the generated content before allowing automated publishing.

---

# 🧠 Why Human Approval Is Included

Fully automated AI publishing can sometimes produce content that is:

* Incorrect
* Repetitive
* Out of context
* Poorly formatted
* Factually inaccurate

This workflow therefore uses a **Human-in-the-Loop** approach.

Instead of:

```text
AI → LinkedIn
```

the architecture is:

```text
AI
 ↓
Human Review
 ↓
Approval
 ↓
LinkedIn
```

This provides an additional quality-control layer.

---

# 🔄 Complete Workflow

The complete process can be summarized as:

```text
┌───────────────────────┐
│  Schedule: 9 AM IST   │
└───────────┬───────────┘
            ↓
┌───────────────────────┐
│ Calculate Campaign Day│
│       1 → 30          │
└───────────┬───────────┘
            ↓
┌───────────────────────┐
│ Select AI Topic       │
└───────────┬───────────┘
            ↓
┌───────────────────────┐
│ OpenAI Generates Post │
└───────────┬───────────┘
            ↓
┌───────────────────────┐
│ Send to Gmail         │
│ for Human Approval    │
└───────────┬───────────┘
            ↓
       ┌────┴────┐
       ↓         ↓
    APPROVE    DECLINE
       ↓         ↓
       ↓      SKIP POST
       ↓
┌───────────────────────┐
│ Publish to LinkedIn   │
└───────────────────────┘
```

---

# 🎯 Use Cases

This automation can be adapted for:

* AI content creation
* LinkedIn personal branding
* Developer education
* Technical content marketing
* AI/ML learning series
* Daily educational posts
* Personal portfolio building
* Human-in-the-loop AI systems
* Social media automation
* n8n workflow learning

---

# 🚀 Future Improvements

Some improvements that could make this automation even more powerful:

* [ ] Store previously published posts in Google Sheets
* [ ] Add duplicate-topic detection
* [ ] Add AI fact-checking
* [ ] Add content quality scoring
* [ ] Add automatic post regeneration
* [ ] Add image generation
* [ ] Add LinkedIn analytics tracking
* [ ] Store post history in a database
* [ ] Add multiple content categories
* [ ] Support multiple social platforms
* [ ] Add automatic failure notifications
* [ ] Add campaign pause/resume functionality
* [ ] Add configurable posting schedules

---

# 📚 Learning Resources

If you are new to n8n, learn these concepts first:

```text
1. Workflows
2. Nodes
3. Triggers
4. Expressions
5. Code nodes
6. Credentials
7. API integrations
8. AI nodes
9. Conditional logic
10. Human-in-the-loop workflows
```

Official n8n resources:

* [n8n Documentation](https://docs.n8n.io/?utm_source=chatgpt.com)
* [n8n Academy](https://learn.n8n.io/?utm_source=chatgpt.com)
* [n8n AI Agents](https://n8n.io/ai-agents/?utm_source=chatgpt.com)
* [n8n Workflow Templates](https://n8n.io/workflows/?utm_source=chatgpt.com)

---

# ⚠️ Responsible Use

This project is intended for **learning, experimentation, and personal automation**.

You are responsible for:

* Reviewing AI-generated content
* Verifying factual claims
* Protecting your credentials
* Following LinkedIn's applicable policies and platform requirements
* Following applicable email and API usage policies
* Avoiding spam or misleading automated content

The human approval step is intentionally included to keep a person in control of publishing.

---

# 👨‍💻 Author

**Jilla Srivardhan**

GitHub: `jillasrivardhan`

This project demonstrates practical experience with:

```text
n8n
AI Automation
OpenAI
Workflow Design
APIs
Gmail Integration
LinkedIn Integration
JavaScript
Human-in-the-Loop AI
```

---

# ⭐ If You Find This Useful

If this project helped you understand AI-powered workflow automation, consider giving the repository a ⭐ and exploring the workflow to build your own automation systems.

---

## 📌 Quick Start

```text
1. Clone/download this repository
2. Open n8n
3. Import the JSON workflow
4. Connect OpenAI
5. Connect Gmail
6. Connect LinkedIn
7. Change the Gmail recipient to your email
8. Test the workflow
9. Review the generated post
10. Approve the test post
11. Verify LinkedIn publishing
12. Activate the workflow
13. Let n8n handle the daily 30-day campaign
```

**Import → Connect Accounts → Test → Approve → Activate → Automate 🚀**
