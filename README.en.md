[🇷🇺 Русская версия](README.md)

# Ivan Ponomarev

20+ years in construction as project manager, PMO lead and scheduler. I build AI products that solve real construction problems - from meeting minutes and team roles to schedule audits and defect control. Over the last year: voice agents with telephony, time series forecasting and infrastructure for AI agents.

## What I do

I design and ship AI systems to production. Not as an IT contractor from the outside, but as someone who spent 20 years building schedules, running site meetings and coordinating subcontractors - and knows where it hurts.

6 products in production. 11 AI agents for real clients. 7 MCP servers. Full cycle: from problem statement to a working corporate service or SaaS with billing.

How I work with AI-generated code: the module contract is written before the code; tests are written by a separate agent that never sees the implementation; I review the full diff every day. That is why six products stay in production without a team.

---

## Products

### [PlanPulse](https://planpulse.ru) - automated construction schedule audit
A project manager uploads a schedule - 30 seconds later gets a verdict: what is wrong, what to fix, how realistic the plan is. No scheduling expertise required.

- Parses **30+ schedule formats** (Primavera P6, MS Project, Asta Powerproject) via MPXJ
- **31 checks** per DCMA-14 and the proprietary PRIM_X methodology
- AI explanations for every check in plain language
- Three interfaces: Telegram bot, Web App, REST API
- Microservice architecture: 8 Docker containers, FastAPI, CI/CD, YooKassa billing
- A companion monitoring service watches all my public projects and catches outages before users complain

`planpulse.ru` | [Telegram Bot](https://t.me/PrimaX_wbs_bot) | [Web App](https://planpulse.ru/app/)

### Voice AI agent with telephony - "mystery shopper" *(private repo, commercial contract)*
A sales quality team orders a check: the agent calls the manager itself, plays a customer following a given script, holds a live voice conversation and returns a recording with a transcript. No human operator on the line. Stages 1 and 2 delivered to the client with acceptance acts and live measurements.

- **One request - one call.** The client's system sends a number and a script; the call happens with no manual steps. Extensions are dialed automatically.
- **A conversation, not a survey.** Speech-to-speech with no "please hold": response gap under 3 seconds. When the person interrupts, the agent goes silent within a second. Measured properly: on a dual-track recording with agent and human on separate channels.
- **Sounds human.** Hesitations, filler words, interjections. Voice, tempo and manner are set per call. Background by choice: street, car, call center. Phone-line degradation on demand.
- **Controlled from outside, on the fly.** Script, mandatory questions, end condition, schedule window, duration limit, retries on no-answer - all are order parameters. Voicemail is detected and never counts as a conversation.
- **Nothing gets lost.** A persistent queue survives restarts. Results arrive as signed webhooks; if the client's server was down, they pull the result themselves with a delivery log. Recordings go straight into the client's storage and self-delete after 7 days.
- **Honest refusal instead of overload.** Line capacity is counted in seconds; an infeasible batch is rejected immediately with a capacity calculation. Retrying an order after a network failure never creates a duplicate call.

Under the hood: OpenAI Realtime as the dialogue engine, Twilio for telephony, FastAPI, a persistent queue, signed webhooks with retries. The interface specification passed external review and FPF hardening: 24 fixes, 3 critical. Five contradictions resolved with TRIZ. Dependencies with verified licenses, CC0 backgrounds. Logs contain neither phone numbers nor conversation text.

### Financial time series forecasting on a foundation model *(private, NDA)*
A trading team gets a weekly forecast for its set of instruments. The model is retrained from scratch every week: each cutoff gets its own dataset, its own model, a forecast for its own week only. That is the defense against peeking into the future.

- **Chronos-2** on local weights via AutoGluon, GPU in a container, 5 years of history, two timeframes
- Production run over **16 cutoffs**, dry-run mode, resume after failure from any cutoff
- Each of 7 modules returns a checked report, not data - the pipeline tells you where it broke
- Candles and forecasts live in **ClickHouse**; delivery to the team moved from files to the database

Two findings that cost more than the code. The old pipeline overwrote the training boundary and made all 18 datasets identical - 9 GPU hours wasted while metrics looked great. The calibrator was reading a bar the model had not yet seen and "improved" the forecast by 20 points. Both closed with guards, not a one-line fix.

### DefectMaster - AI analysis of construction defects
An inspector photographs a defect - the bot identifies the type, rates severity and names the violated SNiP, GOST or SP code. Report generated automatically.

- Image analysis via Google Gemini (Vision)
- Linked to the Russian regulatory base - a specific clause, not an abstract description
- Two products: [stroycontrolbot.ru](https://stroycontrolbot.ru) (B2C) and [stroycontrolai.ru](https://stroycontrolai.ru) (B2B)

### FABLE - room measurement from laser scans *(private repo)*
Upload a point cloud of a room - two minutes later the measurement package is ready: IFC model for Archicad/Revit, DXF floor plan, curvature maps for every wall and floor, rough finishing calculation (plaster, reveals, screed) with quantities and a PDF estimate. Areas are easy to measure - and easy to measure wrong; a scan measures the whole surface, not three tape-measure points.

- Leveling plane chosen by economic optimum: grind the bump or pour extra mortar - the program costs both
- Every figure carries a confidence level: measured / partial / scanner shadow; foreign objects near walls are detected automatically
- Regression on reference scans: 11 metrics with tolerances on every run
- Full run - 1.8 minutes; scanner Leica RTC360, rated accuracy 1.9 mm at 10 m
- Around the pipeline - a mini-CRM: landing page leads, one-click client email from Telegram, site visit calendar, staff chat

### [Shtab](https://protokolov.net) - digitizing construction site meetings
Every week on site there is a coordination meeting. Dozens of action items, deadlines, owners. Minutes live in Word or Excel, get emailed and lost. Shtab fixes that:

- Import existing minutes, create items by voice
- AI help with wording and checklists
- Action item tracking, reminders to owners
- First-pass analysis and feedback on submitted reports
- Email notifications and a Telegram bot
- Analytics dashboard, deadline tracking

### [Loomio AI](https://teamplan.ru) - multi-agent expert environment
Three LLM experts (Claude, Gemini, GPT) reply in turn to a human expert in a thread, each looking at the question from a different angle. Built and used to develop an extended methodology for construction schedule analysis with ~100 experts involved.

### idea-collection - a mechanism base searchable by situation *(private repo)*
Ask "how do we split fairly when one partner put in money and the other put in time" - you get not advice but three to five mechanisms from game theory, mechanism design and stratagems, with examples and countermeasures.

- **2,477 cards** from 30 sources; 26 books digested into summaries by LLM agents
- Own RAG: SQLite index, search by situation description rather than keywords
- **MCP server with 5 tools**: search, card, related, random, bridge to TRIZ
- Link graph of **279 verified edges**; TRIZ map of 40 principles and 204 search terms
- Adversarial review of the core: **284 attacks with countermeasures and 146 reinforcements**
- A methodology shelf for course authors: 152 cards

Maintained under GRACE 4 with autonomous AFK sessions; passed a system-level FPF audit.

### [Belbin Role Test](https://roletest.ru) - team role analysis
The tool I used as a project manager to assemble project teams. Psychometric analysis by the Belbin method: identifies each member's role, shows team balance and suggests who is missing. Helps with hiring and redistributing responsibility. And since HR people use it alongside hard-nosed PMs - there are cats!

### [Fluffy Fox Ear](https://foxear.ru) - transcription and minutes
Corporate SaaS: upload meeting and thesis defense recordings, WhisperX transcription, speaker diarization, structured minutes. Multi-microphone support to pick the best recording, context-aware analysis - for example, against the text of a dissertation. Also used inside [Shtab](https://protokolov.net).

### [vacancy.teamplan.ru](https://vacancy.teamplan.ru) - MVP "Job posting via AI assistant" *(private repo)*
Full-stack MVP for a recruiting startup. A manager describes a position in chat - by voice or text - and AI assembles a structured job posting with sections (requirements, duties, terms), interview tasks and checklists. Three-zone UI: job list ⇆ AI chat ⇆ artifact panel with inline editing and real-time updates over SSE. Voice input with live VU meter, auth hardening, checklists that expand by context.

- Backend: Python 3.12 + FastAPI + SQLAlchemy 2.x async + Alembic + arq + Redis + Instructor + OpenRouter
- Frontend: Next.js 15 + App Router + TypeScript + Vercel AI SDK + TanStack Query + Zustand + shadcn/ui
- Full development cycle under the GRACE framework - from requirements and knowledge graph to verification plan

### Risk Graph - AI-first construction risk management *(private repo)*
Knowledge graph on Neo4j with GraphRAG, chat interface for the risk manager, 2D graph visualization. An AI agent on the knowledge graph: from a natural-language query to a generated Cypher query and interpreted result. Vector search over risk and incident descriptions, linked to building codes.

### Music companion over Yandex Station *(private repo)*
Say to the Station "ask Claude what this track is" - the Station answers in its own voice, not Alice's. Like, dislike, search and playback go through the same loop.

- MCP server `music`: Station remote over the local protocol, likes, search, arbitrary mp3 by URL
- "Ears" via an Alice skill: voice goes to the server, then to the agent, the reply comes back synthesized with loudness normalization
- Standby mode: the agent listens and answers until you say "enough"
- Safety rule built in: by voice only read and reversible actions. Send, delete, pay - only from chat

---

## AI Agents in Production

11 LLM-based agents automating sales, consulting and customer support. Each is not a template chatbot but a system with RAG, integrations and domain understanding.

| Industry | Purpose |
|----------|---------|
| EdTech | Course selection, identifying client needs |
| Professional Development | Program consulting, scheduling Zoom meetings |
| Higher Education | University admissions consultant |
| Travel | Sea cruise consultant |
| Construction | Legal assistance on construction management |
| Corporate Training | Project management assistant |
| Cybersecurity | Expert support for the R-Vision platform |
| Manufacturing | Paint and coating sales manager |
| Marketing | Content planning, trend analysis |
| Finance | Virtual auto pawnshop consultant |
| Security | CCTV system selection, quote preparation |

---

## Open Source / AI Tooling

### [GRACE Framework](https://github.com/Baho73/grace-marketplace-2) - Agent Skills for contract-driven AI development
An open Claude Code plugin: contract first, code second. The model does not "write code" - it implements an approved MODULE_CONTRACT and knowledge graph.

I am a contributor: Hardening Pass 1 (anti-rationalization checklists for agents, evidence-driven verification, knowledge graph integrity checks), and in August 2026 - **an upstream proposal on revertible effects**: every module contract gets EFFECTS and REVERT fields, and the project's effect inventory is assembled automatically. The agent knows not only what a module does but how to undo it. Article in two languages, FPF-verified. Field-tested on claudebar during the GRACE 3 → GRACE 4 migration.

### [claudebar](https://github.com/Baho73/claudebar) - a panel for parallel agent sessions
Rust + Win32, always on top, a switcher between open Claude Code sessions and editors. Version 0.4.1: inbox indicator with source icons (Gmail, Yandex, Mail.ru, Telegram, MAX) - the project row shows what arrived and opens the message on click. "Handled" is set by whoever read it, not by hand. Managed under GRACE 4 with revertible effects in contracts.

### MCP servers - infrastructure for AI agents
A family of Model Context Protocol servers through which my agents reach messengers, email, documents and hardware. I use them daily; some are published.

- **[mcp-telegram](https://github.com/Baho73/mcp-telegram)** - Telegram for Claude: messages, media, reactions, polls, scheduled messages. Hosted version at [mcp-telegram.com](https://mcp-telegram.com), QR login in 30 seconds. GramJS / MTProto.
- **[mcp-gdocs](https://github.com/Baho73/mcp-gdocs)** - Google Docs from Markdown with full formatting (headings, tables, lists, bold/italic).
- **[mcp-server-matrix](https://github.com/Baho73/mcp-server-matrix)** - Matrix: read and send messages, manage rooms.
- **[mcp-server-max](https://github.com/Baho73/mcp-server-max)** - MAX messenger. Plus contributions to [renosaza/max-mcp](https://github.com/renosaza/max-mcp): recovery after a client update, session fingerprint, attachment download.
- **mail-mcp** *(private)* - email over multiple IMAP/SMTP accounts (Gmail, Yandex, Mail.ru, MXroute) with per-requester memory: no message is handed out twice. An inbox router sorts email, Telegram and MAX into project folders and lights the claudebar badge. Mailbox management via DirectAdmin.
- **music** *(private)* - Yandex Station remote, see above.
- **mech** *(private)* - mechanism search in idea-collection, see above.
- **planpulse-mcp** *(private)* - DCMA analysis of .mpp / .xer / .xml schedules straight from an AI agent.

---

## Other projects

### [Analytics Portal](http://147.45.184.55/) | [GitHub](https://github.com/Baho73/WhisperX-Audio-Pipeline)
Business analytics platform: AI call scoring (BANT qualification, DUSHA emotion analysis, manager ranking) + construction dashboard (EVM analysis CPI/SPI, Gantt chart, budget S-curve).
> Demo: `user` / `demo2024`

### Weld Seam Detection | [Demo](https://youtu.be/ie_D0QS-dDo)
Computer vision on a wheel rim production line. YOLOv8 finds the weld seam in real time via laser projection and stops the rotation for precise positioning.

### [AI DevOps Automation](https://github.com/Baho73/ai-devops-automation)
AI agent for deployment automation: 15 seconds instead of 7 minutes. Log analysis, DB migrations, Docker container management over SSH.

### [AeroflotSeg](https://github.com/Baho73/AeroflotSeg)
CV segmentation pipeline (PyTorch, SAM, U2-Net). Specialized in metallic objects with specular highlights.

### [Cluster Optimization](https://github.com/Baho73/cluster-optimization)
Clustering 45K text embeddings. Cleaning with an ensemble (KNN, LOF, Isolation Forest), k selection by four metrics, KMeans + t-SNE.

### [Trebuchet Simulator](https://github.com/Baho73/trebuchet-simulator)
Physics simulator: Lagrangian mechanics, symbolic derivation of equations (SymPy), genetic algorithm optimization. Range 2,840 m.

### [Acoustic Impact Localization](https://github.com/Baho73/acoustic-impact-localization)
Impact point detection by acoustic triangulation. 6 sensors, nonlinear least-squares optimization.

### [XL2MD](https://baho73.github.io/XL2MD/) | [GitHub](https://github.com/Baho73/XL2MD)
Excel -> Markdown converter. Single-file tool with no dependencies.

### [rosreestr2coord](https://github.com/Baho73/rosreestr2coord) - coordinates by cadastral number
Utility: nspd.gov.ru parser, land plot coordinates by cadastral number.

### [tg-contact-extractor](https://github.com/Baho73/tg-contact-extractor) - LLM extraction from Telegram
Structured data extraction from Telegram chat exports via LLM. Customizable prompts per extraction type, JSON and Excel output, dark GUI and CLI.

### [seo-generator](https://github.com/Baho73/seo-generator) - SEO Product Description Generator
Backend service for SEO product descriptions. TypeScript stack: NestJS + LangChain.js + Zod (LLM output validation against schemas) + OpenRouter.

### AudioStend - real-time audio recognition with semantic tagging *(private repo)*
Research bench for real-time audio stream recognition with automatic semantic tagging. Google Cloud STT and WhisperX running in parallel for quality comparison, real-time web visualization of recognized tags.

### EcoAuth (TG_Auth) - centralized Telegram authentication *(private repo)*
Telegram login ecosystem for external apps: Auth Hub, client library, CLI, JWT + FastAPI. Lets third-party services delegate user authentication to Telegram bots.

### HH_AI_Sender - AI automation for hh.ru applications *(private repo)*
Personal AI tool for hh.ru: vacancy search and scoring via OpenRouter against two resumes, individual cover letters based on the job description (no templates), submission via API with a browser fallback for employer tests. Draft pipeline pending → ready → sent, live chat sync every 15 minutes, skip reasons on record, external questionnaires. FastAPI backend + Vite/React frontend + SQLite.

---

## Teaching cases and methodology

I take the test assignments below beyond "it works" into a case study format: problem statement, decisions made and alternatives rejected, measurement, an honest list of what was not done. That turns them into teaching cases rather than portfolio lines.

What is in this set:
- **11 public repositories**, six of them full cases with measured numbers. Automated tests in nine; 370+ where the count is stated.
- **A visible fork instead of a ready answer.** Three document search strategies with a table of tokens, latency and cost. Choosing rules over an LLM with an explanation of why embeddings are the wrong tool here. An honest-refusal threshold calibrated on data and locked by a test.
- **My own mistakes as material.** One case shows how a metric scored 30 out of 30 and why the honest number is 17 out of 30. Another - four places where I was wrong and exactly what caught it.
- **Recurring practices** across cases: honest refusal over guessing, network-free tests on fixtures, a separate "decisions and rejected alternatives" document, a "what I did not do and why" section.

Methodology assets:
- **The guide "From Chat to Agents"** for non-programmers: ~22,000 words, 10 practical recipes in the format "task, prompt, pitfalls, how to verify", 8 agent harness reviews (Claude Code, Codex CLI, Gemini CLI, Cline and others), a sandbox with synthetic data and reference answers. Safety comes first, before installing anything. Built into a single document by script, published at a permanent link, feedback through reader comments.
- **A pipeline for producing teaching materials**: research → backward design from outcomes → three independent checks (composition, TRIZ contradictions, overpromising). Each stage attacks the previous result rather than extending it. Yield on one set: 10 composition defects, 5 resolutions from contradictions, 12 places where the claim outran the evidence.
- **Mentor answers** ([test-07-11](https://github.com/Baho73/test-07-11)): why RAG breaks on real questions and how to measure retrieval and generation separately; a seven-point review of a student's code; a two-to-three-week plan for a stuck learner.
- Case author and reviewer in educational AI projects (under NDA). Loomio AI is used for methodology work with ~100 experts. idea-collection holds a 152-card shelf for course authors.

---

## Test assignments

### [annual-report-qa](https://github.com/Baho73/annual-report-qa) - AI assistant over a company's annual report
Senior AI/ML test: Q&A over a 201-page PDF with provenance down to the page number. Numbers extracted by two independent paths (parser + vision model) and cross-checked. Three search modes - full context, section router, BM25 - measured on a shared question set: cost per answer from $2.11 down to $0.31 at the same quality. Responsibility boundaries built in: no investment advice, an answer without a source is not an answer. Streamlit demo in one command.

### [crown-test-rag](https://github.com/Baho73/crown-test-rag) - RAG with citations and honest refusal
Crown (AI & Data) test: Q&A over a knowledge base. FastAPI, E5 embeddings, FAISS persisted to disk, OpenRouter. The key decision: a relevance threshold. Below it the model is never called and the service replies "the knowledge base has no answer". Tests for chunking, search and the refusal contract. MIT.

### [db-sanitizer](https://github.com/Baho73/db-sanitizer) - PostgreSQL database sanitization
RUSAL test: anonymizing databases before handing them out. The LLM builds a sanitization plan from schema metadata without seeing the data; a deterministic engine (Greenmask) executes it. The model has no access to content, the executor has no room to improvise.

### [position-matcher](https://github.com/Baho73/position-matcher) - job title normalization from 1C
MSTROY test: raw job titles mapped to a classifier of 56 canonical positions. Closed environment - standard library only, no external APIs. Three steps: normalization, domain synonyms, fuzzy scoring. **100% on the labeled sample** (50 of 50); of 300 records 280 matched, 5 flagged for manual review.

### [actflow](https://github.com/Baho73/actflow) - payments, projects and closing documents
Fullstack test: FastAPI + React + PostgreSQL. Bank statement parsing, act statuses, dashboard.

### [vibecheck](https://github.com/Baho73/vibecheck) - request validation for an Agent API
Test: validating requests to the "Vibe Marketer" Agent API against their own catalog - before sending and before money is charged.

### [test-07-11](https://github.com/Baho73/test-07-11) - mentor for the "AI Engineer" course
Test for a mentor position: 6 tasks with answers.

### [splitmate](https://github.com/Baho73/splitmate) - shared group expenses
Test assignment: FastAPI + React + PostgreSQL in Docker. A group tracks shared spending; the service computes who owes whom and proposes the minimal set of transfers. One command to run (`docker compose up`).

### [cbr-currency-toolkit](https://github.com/Baho73/cbr-currency-toolkit) - Bank of Russia exchange rate utilities
A three-part test assignment in one repository:
- **FastAPI web converter** with retry, TTL cache and cross-conversion through the ruble - deployed at [converter.teamplan.ru](https://converter.teamplan.ru).
- **Async CLI** processing Bank of Russia data (daily dynamics, top movers), CSV/JSON export, Docker and instructions.
- **Google Apps Script** - rate export to a Google Sheet on a trigger via UrlFetchApp.

### [fullstack-test-task](https://github.com/Baho73/fullstack-test-task) - File Exchange MVP
Fullstack test: Python backend + React frontend, a file exchange MVP.

---

## Tech Stack

**Backend:** Python, FastAPI, Docker, PostgreSQL, ClickHouse, Rust, CI/CD

**AI/ML:** PyTorch, scikit-learn, YOLOv8, OpenCV, LangChain, FAISS, E5 embeddings, WhisperX, AutoGluon / Chronos-2

**LLM and agents:** OpenAI, Claude, Gemini API, OpenAI Realtime + Twilio (voice and telephony), RAG, prompt engineering, multi-agent systems, MCP, Claude Code, GRACE

**Construction standards:** DCMA-14, PRIM_X, EVM (CPI/SPI), critical path, Primavera P6, MS Project, Spider Project

---

## Contacts

[![Telegram](https://img.shields.io/badge/Telegram-@IvanPonomarev-blue?logo=telegram)](https://t.me/IvanPonomarev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-ivanponomarev-blue?logo=linkedin)](https://linkedin.com/in/ivanponomarev)
