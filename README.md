# 🤖 Autonomous Agentic SEO Blog Writer v2

> **Real-Time US Trending Topics + 7 AI Agents + Beautiful Gradio UI**  
> Fully autonomous pipeline that discovers live trending topics, researches them with real data, and writes publication-ready 1500+ word SEO blog posts — end-to-end, zero manual input.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)
![LangGraph](https://img.shields.io/badge/LangGraph-Multi--Agent-purple?style=flat-square)
![Groq](https://img.shields.io/badge/Groq-LLM%20Inference-orange?style=flat-square)
![Gradio](https://img.shields.io/badge/Gradio-UI-green?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

---

## 📌 What It Does

This project is a **7-agent LangGraph pipeline** that:

1. 🔍 **Discovers** real-time trending US topics using Serper's live Google Search & News API
2. 🧠 **Scores** 8 candidate topics across 5 SEO dimensions to pick the best ranking opportunity
3. 📊 **Researches** the winning topic with 4 targeted web queries — extracting stats, quotes, and US market angles
4. 🔑 **Builds** a full SEO strategy: primary keyword, secondary keywords, long-tail keywords, meta title, meta description, and URL slug
5. ✍️ **Writes** a 1500+ word, fully formatted, US-focused blog post with H2/H3 headings, bullet points, FAQ, and CTA
6. ✅ **Edits** the draft for grammar, flow, keyword density — and scores SEO (0–100) + Readability (0–100)
7. 📱 **Generates** platform-specific captions for Twitter, LinkedIn, and Instagram

All wrapped in a **beautiful dark-themed 6-tab Gradio UI** with one-click Markdown download.

---

## 🖼️ UI Preview

```
┌─────────────────────────────────────────────────────────┐
│  🤖 Autonomous Agentic SEO Blog Writer                  │
│  Real-Time US Trends • 7 AI Agents • LangGraph • Groq  │
├──────────┬──────────────────────────────────────────────┤
│ ⚙️ Niche  │  📝 Blog Post Output (1500+ words)          │
│ dropdown │                                              │
│          │  SEO Score: 85/100                           │
│ 7-Agent  │  Readability: 82/100                         │
│ pipeline │                                              │
│ info     │  [Save as Markdown]                          │
│          │                                              │
│ [LAUNCH] │                                              │
└──────────┴──────────────────────────────────────────────┘
  Tabs: Control Panel | SEO Report | Research | Social | Outline | Log
```

---

## 🏗️ Architecture

```
User Input (Niche + Model)
        │
        ▼
┌───────────────────────────────────────────┐
│           LangGraph StateGraph            │
│                                           │
│  [1] Trend Scout    ← Serper Live Search  │
│         ↓                                 │
│  [2] Topic Analyst  ← 5-dim scoring       │
│         ↓                                 │
│  [3] Researcher     ← 4 web queries       │
│         ↓                                 │
│  [4] SEO Strategy   ← keywords + meta     │
│         ↓                                 │
│  [5] Blog Writer    ← 1500+ word post     │
│         ↓                                 │
│  [6] Editor         ← polish + score      │
│         ↓                                 │
│  [7] Social Media   ← 3 platform caps     │
└───────────────────────────────────────────┘
        │
        ▼
  Gradio UI Output
  (Blog | SEO Report | Research | Social | Outline | Log)
```

---

## 🤖 The 7 Agents

| # | Agent | Role | Key Output |
|---|-------|------|------------|
| 1 | **Trend Scout** | Fires 5 real-time Serper queries (web + news) for today's US trends | 8 trending topic candidates |
| 2 | **Topic Analyst** | Scores all topics on search volume, competition, US relevance, monetisation, timeliness | Winning topic + rationale |
| 3 | **Researcher** | 4 targeted deep-dive queries — extracts stats, expert insights, US business angle | Research brief + 5 key stats |
| 4 | **SEO Strategy** | Analyses competitor titles, builds full keyword map and blog outline | Meta tags, keywords, slug, H-structure |
| 5 | **Blog Writer** | Writes complete 1500+ word post following the outline, with FAQ + CTA | Full Markdown blog post |
| 6 | **Editor** | Proofreads, strengthens keyword density, scores the post | Polished post + SEO/readability scores |
| 7 | **Social Media** | Writes platform-optimised captions with hashtags and CTAs | Twitter + LinkedIn + Instagram captions |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Groq API** | Ultra-fast LLM inference — `llama-3.1-8b-instant`, `llama-3.3-70b-versatile`, `mixtral-8x7b-32768` |
| **LangGraph** | Multi-agent orchestration via `StateGraph` with `TypedDict` shared state |
| **LangChain + LangChain-Groq** | LLM chains: `ChatPromptTemplate → ChatGroq → StrOutputParser` |
| **Serper API** | Real-time Google Search (`/search`) and Google News (`/news`) endpoints |
| **Gradio** | 6-tab interactive dark UI with live status, file download, and agent log |

---

## ⚡ Quickstart

### 1. Get Your API Keys (both free tiers available)

- **Groq API Key** → [console.groq.com](https://console.groq.com) *(free, fast inference)*
- **Serper API Key** → [serper.dev](https://serper.dev) *(2,500 free searches/month)*

### 2. Install Dependencies

```bash
pip install groq langgraph langchain langchain-groq langchain-community gradio requests
```

### 3. Run the Notebook

Open `Agentic_SEO_Blog_Writer_v2.ipynb` in **Jupyter** or **Google Colab** and run all cells top-to-bottom.

### 4. Enter API Keys

You'll be prompted securely via `getpass` — keys are never stored in the notebook:

```
Groq API Key   -> https://console.groq.com :  ········
Serper API Key -> https://serper.dev        :  ········
```

### 5. Launch the UI

Gradio launches automatically. A **public share link** is also generated for remote access:

```
Running on local URL:  http://127.0.0.1:7860
Running on public URL: https://xxxx.gradio.live
```

Pick your niche → click **LAUNCH AUTONOMOUS PIPELINE** → wait ~60 seconds.

---

## 🎛️ Configuration

At the top of the pipeline cell, you can change the default model:

```python
MODEL = 'llama-3.1-8b-instant'   # Fast (default)
# MODEL = 'llama-3.3-70b-versatile'  # Best quality
# MODEL = 'mixtral-8x7b-32768'       # Strong reasoning
```

Available niches (or type your own custom niche in the UI):

```
Technology & AI · Digital Marketing · Finance & Investing · Health & Wellness
E-commerce & Retail · Real Estate · Cybersecurity · Startups & Entrepreneurship
Remote Work · Sustainability & Green Tech · (+ any custom niche)
```

---

## 📂 Project Structure

```
📦 Agentic-SEO-Blog-Writer/
├── 📓 Agentic_SEO_Blog_Writer_v2.ipynb   ← Main notebook (run this)
├── 📄 README.md                           ← You are here
└── 📊 Agentic_SEO_Blog_Writer.pptx        ← Project presentation (optional)
```

---

## 📤 Output Examples

After one pipeline run you get all of the following:

**Blog Post Tab**
```markdown
# Why Agentic AI Is Reshaping the US Workforce in 2026

As of March 2026, over 67% of Fortune 500 companies have deployed...
## What Is Agentic AI?
## Key Statistics You Need to Know
## Real US Company Examples
...
## FAQ
...
```

**SEO Report Tab**
```
Primary Keyword  : agentic ai us workforce 2026
Secondary KWs    : ai automation jobs, llm enterprise adoption, ...
Meta Title       : Agentic AI & the US Workforce: 2026 Guide (58 chars)
Meta Description : How agentic AI is transforming American jobs... (142 chars)
URL Slug         : agentic-ai-us-workforce-2026
SEO Score        : 87/100
Readability      : 83/100
```

**Social Media Tab**
```
TWITTER  : 🚨 67% of Fortune 500s are already deploying Agentic AI.
           Is your team ready? Full breakdown → [link] #AgenticAI #FutureOfWork #AI2026

LINKEDIN : The US workforce is at an inflection point...
           [3-paragraph professional post with data + CTA]

INSTAGRAM: Agentic AI isn't coming — it's here 🤖
           Here's what every American professional needs to know 👇
           #AgenticAI #AITrends #FutureOfWork #Tech2026 #USBusiness
```

---

## 🔒 Security Notes

- API keys are entered via `getpass` and stored only in memory for the session
- Keys are **never written** to the notebook or any file
- Do **not** hardcode API keys directly into the notebook before pushing to GitHub

---

## 📋 Requirements

```
groq
langgraph
langchain
langchain-groq
langchain-community
gradio
requests
```

Python **3.8+** required.

---



## 📜 License

MIT License — free to use, modify, and distribute.

---

## ⭐ Star This Repo

If this project helped you, please give it a ⭐ — it helps others find it!
