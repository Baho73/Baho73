# Ivan Ponomarev

Python developer. I build AI products end-to-end: from concept to production-ready services.

## Tech Stack

**Core:** Python, TypeScript, SQL (PostgreSQL, SQLite, MySQL)

**Data Science:** pandas, numpy, scikit-learn, matplotlib, seaborn, Jupyter, clustering, t-SNE

**Scientific Computing:** SciPy, SymPy, Lagrangian mechanics, optimization (genetic algorithms, least squares)

**AI/ML:** PyTorch, TensorFlow, SKLearn, YOLOv8, Google Gemini, WhisperX, speaker diarization, emotion analysis, computer vision

**RAG:** FAISS, vector databases, embeddings, document search, [Docling](https://github.com/Baho73/docling) (PDF→Markdown), [DolphinPDF](https://github.com/Baho73/DolphinPDF) (Document Image Parsing)

**Backend:** aiogram, FastAPI, Docker, SSH automation, systemd

**Integrations:** Telegram Bot API, Google Sheets/Drive API, Tinkoff API

**DevOps:** Docker, CI/CD, deployment automation via Python + SSH

## Projects

### [Fluffy Fox Ear](https://foxear.ru) | [GitHub](https://github.com/Baho73/Fluffy-Fox-Ear)
Enterprise SaaS for transcribing dissertation defenses. Full pipeline: audio upload, transcription, speaker diarization, and protocol generation.
`Python` `TypeScript` `Docker`

### DefectMaster Bot — [stroycontrolbot.ru](https://stroycontrolbot.ru) | [stroycontrolai.ru](https://stroycontrolai.ru) | [GitHub](https://github.com/Baho73/DefectMaster-Bot)
Telegram bot for automated detection of construction defects from photos. AI analysis via Google Gemini with references to Russian building codes (SNiP, GOST, SP). Auto-generates reports in Google Sheets. Built-in balance system with payments via Tinkoff.
- **stroycontrolbot.ru** — for individuals
- **stroycontrolai.ru** — for businesses

`Python` `aiogram` `Google Gemini` `Google Sheets API` `Tinkoff API`

### Analytics Portal | [GitHub](https://github.com/Baho73/WhisperX-Audio-Pipeline)
Business analytics platform with two dashboards:

**Call Analytics** — sales call analysis. AI-powered call quality scoring, BANT lead qualification, conversion funnel, emotion analysis (DUSHA model), manager ranking, sales script adherence, and objection handling.
`React` `Chart.js` `BANT scoring` `emotion analysis`

**Construction Dashboard** — construction project management. EVM analysis (CPI/SPI), Gantt chart with drill-down, budget S-curve, task and assignee monitoring.
`Chart.js` `EVM` `Gantt` `S-Curve`

**WhisperX Audio Pipeline** — backend transcription pipeline: speech recognition (WhisperX), speaker diarization, emotion analysis. Processes recordings of meetings, calls, and interviews.

`Python` `WhisperX` `speaker diarization` `emotion analysis` `FastAPI`

### [AI DevOps Automation](https://github.com/Baho73/ai-devops-automation)
AI agent for automating DevOps operations. Deploy in 15 sec instead of 7 min, log analysis in 10 sec, DB migrations in 30 sec. The agent reads scripts and .env files, connects via SSH, and manages Docker containers.
`Python` `LLM` `Docker` `SSH` `Paramiko`

### [AeroflotSeg](https://github.com/Baho73/AeroflotSeg)
CV pipeline for object segmentation using PyTorch neural networks: bounding box detection, cropping, resizing, and final segmentation (rembg, SAM, U2-Net). Specialized in metallic objects with specular highlights — model selection and comparison for challenging cases. *Hackathon project.*
`Python` `PyTorch` `OpenCV` `SAM` `U2-Net` `computer vision`

### [Cluster Optimization](https://github.com/Baho73/cluster-optimization)
End-to-end DS pipeline for clustering 45K text embeddings. Data cleaning via an ensemble of 3 methods (KNN, LOF, Isolation Forest), optimal k selection using 4 metrics (Elbow, Silhouette, Calinski-Harabasz, Davies-Bouldin), final KMeans clustering + t-SNE visualization.
`Python` `scikit-learn` `pandas` `matplotlib` `t-SNE` `KMeans`

### [Trebuchet Simulator](https://github.com/Baho73/trebuchet-simulator)
Physics simulator for a 4-degree-of-freedom trebuchet. Lagrangian mechanics, symbolic derivation of equations of motion via SymPy, auto-generated NumPy code. Design optimization using a genetic algorithm (differential evolution). Result: 2,840 m range with all constraints satisfied.
`Python` `NumPy` `SciPy` `SymPy` `Matplotlib`

### [Acoustic Impact Localization](https://github.com/Baho73/acoustic-impact-localization)
Determining the point of impact on a surface via acoustic triangulation. 6 sensors, nonlinear optimization (least squares), result visualization.
`Python` `NumPy` `SciPy` `Matplotlib`

### Weld Seam Detection | [Demo](https://youtu.be/ie_D0QS-dDo)
Computer vision system for a wheel rim production line. Real-time weld seam detection using laser projection and YOLOv8. Determines seam position for precise alignment — the valve hole is drilled on the exact opposite side. Controls disc rotation: stops at the target position.
`Python` `YOLOv8` `OpenCV` `computer vision` `industrial automation`

### [XL2MD](https://baho73.github.io/XL2MD/) | [GitHub](https://github.com/Baho73/XL2MD)
Excel to Markdown table converter. Single-file web tool — paste from Excel/Google Sheets, get a formatted Markdown table. No dependencies, no server.
`JavaScript` `HTML` `GitHub Pages`

### [Belbin Role Test](https://roletest.ru)
Web application for identifying team roles based on the Belbin model. Full backend with PostgreSQL, Docker deployment.
`Python` `PostgreSQL` `Docker` `JavaScript`

## AI Agents in Production

11 LLM-based AI agents deployed to production. Automating sales, consulting, and customer support across various industries:

| Industry | Purpose |
|----------|---------|
| EdTech | Course selection, identifying client needs |
| Professional Development | Program consulting, scheduling Zoom meetings |
| Higher Education | University admissions consultant |
| Travel | Sea cruise consultant, booking assistance |
| Construction | Legal assistance and construction management advice |
| Corporate Training | Project management testing and training assistant |
| Cybersecurity | Platform consultant, expert support |
| Manufacturing/Sales | Paint and coating sales, product selection |
| Marketing | Content planning, niche trend analysis |
| Finance | Virtual auto pawnshop consultant |
| Security | CCTV and intercom system selection, quote preparation |

`Python` `aiogram` `LLM` `AI Agents` `Prompt Engineering` `RAG` `Google Sheets API`

## Contacts

[![Telegram](https://img.shields.io/badge/Telegram-@IvanPonomarev-blue?logo=telegram)](https://t.me/IvanPonomarev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-ivanponomarev-blue?logo=linkedin)](https://linkedin.com/in/ivanponomarev)
