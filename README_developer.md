[🇬🇧 English version](README.en.md)

> **Два взгляда на один профиль:**
> [Архитектор / Product Manager](README.md) | **Разработчик** *(вы здесь)*

# Ivan Ponomarev

Python-разработчик. Строю AI-продукты: от идеи до работающего сервиса на проде.

## Стек

**Основное:** Python, TypeScript, SQL (PostgreSQL, SQLite, MySQL)

**Data Science:** pandas, numpy, scikit-learn, matplotlib, seaborn, Jupyter, кластеризация, t-SNE

**Scientific Computing:** SciPy, SymPy, Lagrangian mechanics, optimization (genetic algorithms, least squares)

**AI/ML:** PyTorch, TensorFlow, SKLearn, YOLOv8, Google Gemini, WhisperX, speaker diarization, emotion analysis, computer vision

**RAG:** FAISS, векторные БД, embeddings, поиск по документам, [Docling](https://github.com/Baho73/docling) (PDF→Markdown), [DolphinPDF](https://github.com/Baho73/DolphinPDF) (Document Image Parsing)

**AI-агенты:** Claude Code, MCP (Model Context Protocol), Codex CLI, multi-agent orchestration, contract-driven generation

**Backend:** aiogram, FastAPI, Docker, SSH-автоматизация, systemd

**Интеграции:** Telegram Bot API, Google Sheets/Drive API, Tinkoff API

**DevOps:** Docker, CI/CD, автоматизация деплоя через Python + SSH

## Проекты

### [Fluffy Fox Ear](https://foxear.ru) *(private repo)*
Корпоративный SaaS для транскрибации защит диссертаций. Полный цикл: загрузка аудио, транскрибация, диаризация спикеров, генерация протоколов.
`Python` `TypeScript` `Docker`

### [PlanPulse](https://planpulse.ru) — [Telegram Bot](https://t.me/PlanPulseBot) | [Web App](https://planpulse.ru/app/) | *(private repo)*
Продакшн-сервис для автоматического аудита расписаний строительных проектов. Микросервисная архитектура из 8 Docker-контейнеров: парсер 30+ форматов (Primavera P6, MS Project, Asta Powerproject и др. через MPXJ Java-мост), граф зависимостей, критический путь, 31 проверка по стандарту DCMA-14 и авторской методике PRIM_X. AI-пояснения через OpenRouter, экспорт отчётов в Google Docs, визуальный HTML-дашборд. Три интерфейса: Telegram-бот, веб-приложение (SPA), REST API. Биллинг через ЮKassa + Telegram Stars, админ-панель, корпоративный портал. CI/CD с автодеплоем на VPS.
`Python` `FastAPI` `Docker` `MPXJ` `aiogram` `Google Docs API` `OpenRouter` `nginx` `DCMA-14`

### DefectMaster Bot — [stroycontrolbot.ru](https://stroycontrolbot.ru) | [stroycontrolai.ru](https://stroycontrolai.ru) | *(private repo)*
Telegram-бот для автоматического выявления строительных дефектов по фото. AI-анализ через Google Gemini с привязкой к нормам РФ (СНиП, ГОСТ, СП). Автогенерация отчётов в Google Таблицы. Встроенная система балансов и оплата через Tinkoff.
- **stroycontrolbot.ru** — для физических лиц
- **stroycontrolai.ru** — для юридических лиц

`Python` `aiogram` `Google Gemini` `Google Sheets API` `Tinkoff API`

### [Штаб](https://protokolov.net) — Система управления строительными совещаниями | *(private repo)*
SaaS для цифровизации протокола строительного штаба с AI-слоем. Автоматическое формирование протоколов совещаний, контроль поручений, отслеживание сроков исполнения. Интеграция с процессами стройки.
`Python` `FastAPI` `Docker` `AI` `PostgreSQL`

### [vacancy.teamplan.ru](https://vacancy.teamplan.ru) — MVP «Ввод вакансии через AI-помощника» | *(private repo)*
Full-stack MVP для рекрутингового стартапа. Руководитель в чате описывает позицию голосом или текстом — AI собирает структурированную вакансию с разделами (требования, обязанности, условия), задачи на интервью и чек-листы. 3-зонный UI: список вакансий ⇆ чат с AI ⇆ панель артефакта с inline-edit и real-time обновлениями через SSE.

**Backend**: Python 3.12 + FastAPI + SQLAlchemy 2.x async + Alembic + arq + Redis + Instructor + OpenRouter. Async-воркеры для генерации артефактов, полное логирование.

**Frontend**: Next.js 15 + App Router + TypeScript + AI SDK Vercel + TanStack Query + Zustand + shadcn/ui. Voice-input с live VU-meter, inline-edit полей артефакта, SSE для real-time обновлений из бэкенда.

**Workflow**: полный цикл разработки по фреймворку GRACE — requirements, knowledge-graph, technology, development-plan, verification-plan, design-doc 2500+ строк как обязательный input.

`Python 3.12` `FastAPI` `SQLAlchemy 2 async` `Next.js 15` `TypeScript` `AI SDK Vercel` `OpenRouter` `arq` `Redis` `Zustand` `shadcn/ui` `GRACE` `SSE`

### Risk Graph — AI-first управление строительными рисками | *(private repo)*
Knowledge graph на Neo4j + chat-интерфейс + 2D-визуализация графа рисков. AI-агент-навигатор: от запроса на естественном языке через генерацию Cypher-запроса до интерпретации результата. Векторный поиск по описаниям рисков и инцидентов, привязка к строительным нормам.
`Python` `FastAPI` `Neo4j` `Cypher` `GraphRAG` `LangChain` `vector search`

### [Loomio AI](https://teamplan.ru) — Мультиагентная экспертная среда | *(private repo)*
Экспертная среда на базе self-hosted Loomio с **тремя AI-экспертами** (Claude 4.6, Gemini 3.1 Pro, GPT 5.4). Когда человек-эксперт пишет в тред, ему по очереди отвечают три LLM, рассматривая вопрос с разных сторон. Создаёт коллаборативную среду для обсуждения сложных вопросов между человеком и тремя ИИ. Применяется для разработки расширенной методики анализа строительных графиков (с 31 до 100 пунктов проверки).
`Ruby` `Loomio` `Claude API` `Gemini API` `OpenAI API` `Multi-Agent AI`

### [Analytics Portal](http://147.45.184.55/) | [GitHub](https://github.com/Baho73/WhisperX-Audio-Pipeline)
Платформа бизнес-аналитики с двумя дашбордами:

**Call Analytics** — анализ телефонных переговоров отдела продаж. AI-скоринг качества звонков, BANT-квалификация лидов, воронка конверсии, эмоциональный анализ (модель DUSHA), рейтинг менеджеров, следование скрипту продаж, обработка возражений.
`React` `Chart.js` `BANT scoring` `emotion analysis`

**Construction Dashboard** — управление строительными проектами. EVM-анализ (CPI/SPI), диаграмма Ганта с drill-down, S-кривая освоения бюджета, мониторинг задач и ответственных.
`Chart.js` `EVM` `Gantt` `S-Curve`

**WhisperX Audio Pipeline** — бэкенд-пайплайн транскрибации: распознавание речи (WhisperX), диаризация спикеров, анализ эмоций. Обработка аудиозаписей совещаний, звонков и интервью.
> Demo: `user` / `demo2024`

`Python` `WhisperX` `speaker diarization` `emotion analysis` `FastAPI`

## Open Source / AI Tooling

### [GRACE Framework](https://github.com/Baho73/grace-marketplace-2) — Agent Skills для contract-driven AI-разработки
Открытый Claude Code плагин для AI-engineering методологии. Автор @osovv. Я contributor: сделал Hardening Pass 1 для своего fork'а:
- **anti-rationalization чек-листы** для AI-агентов — заставляют модель проверять свой выход против evidence-цитат до финального ответа.
- **evidence-driven verification** — валидация результатов LLM против реального состояния кода и тестов, а не «мне кажется».
- **knowledge-graph integrity validation** — проверка целостности графа знаний модулей при генерации.

Формализация «контракт-первый» подхода для AI-генерации кода: сначала MODULE_CONTRACT, потом knowledge graph, потом код. Меняет паттерн работы с LLM-coder'ом — модель не «пишет код», а реализует утверждённый контракт. На моих рабочих задачах заметно снизило количество правок после генерации.

`Claude Code` `Agent Skills` `AI-driven development` `knowledge graphs` `contract-first`

### MCP servers — Model Context Protocol для AI-агентов
Семейство серверов MCP для подключения LLM к мессенджерам и сервисам. Использую сам в работе с Claude Code / Claude Desktop / Codex CLI, опубликовал в open source.

- **[mcp-telegram](https://github.com/Baho73/mcp-telegram)** — подключение Telegram к Claude. Сообщения, медиа, реакции, опросы, scheduled messages и др. Hosted-версия: [mcp-telegram.com](https://mcp-telegram.com), QR-логин за 30 секунд. На основе GramJS / MTProto.
- **[mcp-gdocs](https://github.com/Baho73/mcp-gdocs)** — MCP server для создания и обновления Google Docs из Markdown с полным форматированием (заголовки, таблицы, списки, bold/italic).
- **[mcp-server-matrix](https://github.com/Baho73/mcp-server-matrix)** — Matrix: чтение и отправка сообщений, управление комнатами через Model Context Protocol.
- **[mcp-server-max](https://github.com/Baho73/mcp-server-max)** — Max (VK Teams) messenger: чтение/отправка сообщений, управление чатами.
- **planpulse-mcp** *(private)* — MCP-сервер (stdio, Python) для интеграции Claude Code с PlanPulse: DCMA-анализ календарно-сетевых моделей .mpp / .xer / .xml прямо из AI-агента.

`MCP` `TypeScript` `Python` `GramJS` `MTProto` `Claude Code integration`

## Другие проекты

### [AI DevOps Automation](https://github.com/Baho73/ai-devops-automation)
AI-агент для автоматизации DevOps-операций. Деплой за 15 сек вместо 7 мин, анализ логов за 10 сек, миграции БД за 30 сек. Агент читает скрипты и .env, подключается по SSH, управляет Docker-контейнерами.
`Python` `LLM` `Docker` `SSH` `Paramiko`

### [AeroflotSeg](https://github.com/Baho73/AeroflotSeg)
CV-пайплайн сегментации объектов на фото с использованием нейросетей PyTorch: детекция bbox, кроп, ресайз и финальная сегментация (rembg, SAM, U2-Net). Специализация на металлических объектах с бликами — подбор и сравнение моделей для сложных кейсов.
`Python` `PyTorch` `OpenCV` `SAM` `U2-Net` `computer vision`

### [Cluster Optimization](https://github.com/Baho73/cluster-optimization)
Полный DS-пайплайн кластеризации 45K текстовых эмбеддингов. Очистка данных ансамблем из 3 методов (KNN, LOF, Isolation Forest), подбор оптимального k четырьмя метриками (Elbow, Silhouette, Calinski-Harabasz, Davies-Bouldin), финальная кластеризация KMeans + t-SNE визуализация.
`Python` `scikit-learn` `pandas` `matplotlib` `t-SNE` `KMeans`

### [Trebuchet Simulator](https://github.com/Baho73/trebuchet-simulator)
Физический симулятор требушета с 4 степенями свободы. Лагранжева механика, символьный вывод уравнений движения через SymPy, автогенерация NumPy-кода. Оптимизация конструкции генетическим алгоритмом (differential evolution). Результат: дальность 2 840 м при соблюдении всех ограничений.
`Python` `NumPy` `SciPy` `SymPy` `Matplotlib`

### [Acoustic Impact Localization](https://github.com/Baho73/acoustic-impact-localization)
Определение точки удара на поверхности методом акустической триангуляции. 6 датчиков, нелинейная оптимизация (least squares), визуализация результатов.
`Python` `NumPy` `SciPy` `Matplotlib`

### Weld Seam Detection | [Demo](https://youtu.be/ie_D0QS-dDo)
Система компьютерного зрения для производственной линии колёсных дисков. Детекция сварного шва в реальном времени через лазерную проекцию и YOLOv8. Определяет положение шва для точного позиционирования — отверстие под ниппель сверлится строго с противоположной стороны. Управление вращением диска: остановка при достижении нужной позиции.
`Python` `YOLOv8` `OpenCV` `computer vision` `industrial automation`

### [XL2MD](https://baho73.github.io/XL2MD/) | [GitHub](https://github.com/Baho73/XL2MD)
Конвертер таблиц Excel в Markdown. Однофайловый веб-инструмент — вставляете из Excel/Google Sheets, получаете готовую Markdown-таблицу. Без зависимостей, без сервера.
`JavaScript` `HTML` `GitHub Pages`

### [rosreestr2coord](https://github.com/Baho73/rosreestr2coord) — координаты по кадастровому номеру
Утилита: парсер сайта nspd.gov.ru, выгрузка координат земельного участка по кадастровому номеру. Для интеграции с ГИС-системами и автоматизации работы с проектной документацией.
`Python` `parser` `Росреестр`

### [tg-contact-extractor](https://github.com/Baho73/tg-contact-extractor) — LLM-extraction из Telegram-экспортов
Утилита для извлечения структурированных данных (контакты, события, темы) из текстовых экспортов Telegram-чатов через LLM. Кастомизируемые промпты под разные типы извлечения, вывод в JSON и Excel, тёмный GUI и CLI.
`Python` `LLM` `prompt engineering` `JSON` `Excel`

### [seo-generator](https://github.com/Baho73/seo-generator) — SEO Product Description Generator
Backend-сервис генерации SEO-описаний товаров. Демонстрация TypeScript-стека: NestJS + LangChain.js + Zod (валидация выхода LLM против схем) + OpenRouter для роутинга между моделями.
`TypeScript` `NestJS` `LangChain.js` `Zod` `OpenRouter`

### AudioStend — стенд распознавания аудиопотока с семантическим тегированием | *(private repo)*
Исследовательский стенд для распознавания аудиопотока в реальном времени с автоматическим семантическим тегированием. Параллельная работа Google Cloud STT и WhisperX для сравнения качества, real-time веб-визуализация распознанных тегов.
`Python` `WhisperX` `Google Cloud STT` `real-time` `web visualization`

### EcoAuth / TG_Auth — централизованная Telegram-аутентификация | *(private repo)*
Экосистема входа через Telegram для внешних приложений: Auth Hub (центральный сервис), клиентская библиотека для интеграции, CLI для управления, JWT-токены, FastAPI backend. Позволяет сторонним сервисам делегировать аутентификацию пользователей через Telegram-ботов.
`Python` `FastAPI` `JWT` `Telegram Bot API` `aiogram`

### HH_AI_Sender — AI-автоматизация откликов на hh.ru | *(private repo)*
Личный AI-инструмент для работы с hh.ru. Парсинг вакансий по двум резюме параллельно (КСП + ML), AI-скоринг релевантности через локальный Ollama LLM, AI-генерация индивидуальных сопроводительных писем на основе описания вакансии (без шаблонов), отправка через браузерную автоматизацию.

Backend: FastAPI + SQLite + фоновые воркеры (loader / scorer / sender) с pause-resume. Frontend: Vite + React + AG Grid. Pipeline черновиков: pending → ready → sent → errors / test_required.
`Python` `FastAPI` `Vite` `React` `Ollama` `Playwright` `SQLite` `AG Grid`

### [Belbin Role Test](https://roletest.ru) *(private repo)*
Веб-приложение для определения командных ролей по Белбину. Полноценный бэкенд с PostgreSQL, Docker-деплой.
`Python` `PostgreSQL` `Docker` `JavaScript`

## Тестовые задания

### [cbr-currency-toolkit](https://github.com/Baho73/cbr-currency-toolkit) — утилиты курсов валют ЦБ РФ
Тестовое задание из трёх частей в одном репозитории (полный цикл за один заход):

1. **FastAPI веб-конвертер валют** — асинхронный HTTP-клиент с retry, TTL-кэш, кросс-конвертация через рубль с учётом номинала. Развёрнут: [converter.teamplan.ru](https://converter.teamplan.ru).
2. **Async CLI-аналитик** — обработка данных ЦБ РФ (суточная динамика, топ движений, агрегаты), экспорт в CSV/JSON, Dockerfile, requirements.txt, инструкция по запуску.
3. **Google Apps Script** — выгрузка курсов в Google Таблицу по триггеру через UrlFetchApp, обработка ошибок, запись статуса в отдельную колонку.

`Python` `FastAPI` `async` `Docker` `Google Apps Script`

### [fullstack-test-task](https://github.com/Baho73/fullstack-test-task) — File Exchange MVP
Тестовое задание fullstack: Python backend + React frontend. MVP файлового обмена с загрузкой, хранением и выдачей файлов.
`Python` `React` `fullstack`

## AI-агенты в продакшене

11 ИИ-агентов на базе LLM, задеплоенных в продакшен. Автоматизация продаж, консультаций и клиентской поддержки в различных отраслях:

| Агент | Сфера | Задача |
|-----|-------|--------|
| [Цифриум](https://t.me/mvp_cifrium_bot) | EdTech | Подбор программ обучения, выявление потребностей клиентов |
| [Промышленный Университет](https://t.me/DPO_Poly_bot) | ДПО | Консультация по программам, назначение ZOOM-встреч |
| [Московский Политех](https://t.me/Politeh_FAQ_test_v2_bot) | Высшее образование | Консультант по зачислению в университет |
| [CruClub](https://t.me/cruclub_test_bot) | Туризм | Консультант по морским круизам для [cruclub.ru](https://www.cruclub.ru/) |
| [Застройщик](https://t.me/Developer_consultant_bot) | Строительство | Юридическая помощь и советы по организации строительства |
| [Евраз PM](https://t.me/evraz_pm_bot) | Корпоративное обучение | Помощник по тестам и обучению управлению проектами |
| R-Vision | Кибербезопасность | Консультант по системе R-Vision, экспертная поддержка |
| [Лакокрасочный завод](https://t.me/Paint_test_sales_bot) | Производство/Продажи | Менеджер по продаже ЛКМ, подбор краски и материалов |
| Контент-менеджер | Маркетинг | Составление контент-планов, анализ трендов под нишу |
| [Автоломбард](https://t.me/autolombars_bot) | Финансы | Виртуальный консультант автоломбардов |
| [Видеонаблюдение](https://t.me/b0095_cam_bot) | Безопасность | Подбор систем видеонаблюдения и домофонов, подготовка КП |

`Python` `aiogram` `LLM` `AI Agents` `Prompt Engineering` `RAG` `Google Sheets API`

## Контакты

[![Telegram](https://img.shields.io/badge/Telegram-@IvanPonomarev-blue?logo=telegram)](https://t.me/IvanPonomarev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-ivanponomarev-blue?logo=linkedin)](https://linkedin.com/in/ivanponomarev)
