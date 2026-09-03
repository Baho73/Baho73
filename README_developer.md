[🇬🇧 English version](README.en.md)

> **Два взгляда на один профиль:**
> [Архитектор / Product Manager](README.md) | **Разработчик** *(вы здесь)*

# Ivan Ponomarev

Python-разработчик. Строю AI-продукты: от идеи до работающего сервиса на проде. Шесть продуктов в проде держу один, без команды - за счёт дисциплины работы с AI-агентами: контракт модуля до кода, тесты пишет отдельный агент и не показывает их кодирующему, дифф ревьюю каждый день.

## Стек

**Основное:** Python, TypeScript, Rust, SQL (PostgreSQL, SQLite, ClickHouse, MySQL)

**Data Science:** pandas, numpy, scikit-learn, matplotlib, seaborn, Jupyter, кластеризация, t-SNE

**Time Series:** AutoGluon, Chronos-2 (foundation-модель на локальных весах), rolling-переобучение, поиск утечек данных

**Scientific Computing:** SciPy, SymPy, Lagrangian mechanics, optimization (genetic algorithms, least squares)

**AI/ML:** PyTorch, TensorFlow, YOLOv8, Google Gemini, WhisperX, speaker diarization, emotion analysis, computer vision

**RAG:** FAISS, E5-эмбеддинги, чанкинг по смысловым блокам с метаданными, порог честного отказа, [Docling](https://github.com/Baho73/docling) (PDF→Markdown), [DolphinPDF](https://github.com/Baho73/DolphinPDF)

**Голос и телефония:** OpenAI Realtime (речь-в-речь), Twilio, barge-in, AMD, двухдорожечная запись, transcript timecodes

**AI-агенты:** Claude Code, MCP (Model Context Protocol), Codex CLI, multi-agent orchestration, contract-driven generation (GRACE), FPF, ТРИЗ

**Backend:** aiogram, FastAPI, Celery + Redis, Docker, SSH-автоматизация, systemd, AmneziaWG

**Интеграции:** Telegram Bot API, Google Sheets/Drive API, Tinkoff API, ЮKassa, IMAP/SMTP, DirectAdmin

**DevOps:** Docker, CI/CD, автоматизация деплоя через Python + SSH, свой мониторинг всех прод-проектов

## Проекты

### [PlanPulse](https://planpulse.ru) - [Telegram Bot](https://t.me/PrimaX_wbs_bot) | [Web App](https://planpulse.ru/app/) | *(private repo)*
Продакшн-сервис для автоматического аудита расписаний строительных проектов. Микросервисная архитектура из 8 Docker-контейнеров: парсер 30+ форматов (Primavera P6, MS Project, Asta Powerproject и др. через MPXJ Java-мост), граф зависимостей (NetworkX), критический путь, 31 проверка по стандарту DCMA-14 и авторской методике PRIM_X. AI-пояснения через OpenRouter, экспорт отчётов в Google Docs, визуальный HTML-дашборд. Три интерфейса: Telegram-бот, веб-приложение (SPA), REST API. Биллинг через ЮKassa + Telegram Stars, админ-панель, корпоративный портал. CI/CD с автодеплоем на VPS. Рядом живёт сервис мониторинга, который следит за всеми моими публичными проектами, и AmneziaWG-сайдкар для Telegram с заблокированных хостингов.
`Python` `FastAPI` `Docker` `MPXJ` `NetworkX` `aiogram` `Google Docs API` `OpenRouter` `nginx` `DCMA-14`

### Голосовой AI-агент с телефонией - «тайный покупатель» | *(private repo, коммерческий заказ)*
Исходящие звонки менеджерам по продажам: агент играет клиента по сценарию, ведёт живой диалог речь-в-речь, отдаёт запись и транскрипт с ролями и таймкодами. Этапы 1 и 2 сданы заказчику с актами и живыми замерами.

Что внутри: `POST /v1/calls` с идемпотентностью по `order_id` (повтор → 200, изменённое тело → 409); DTMF-донабор добавочного; конечный автомат статусов с `status_history`; barge-in ≤1 с (замер по двухдорожечной отладочной записи, агент и собеседник раздельно); пауза ответа ≤3 с; AMD - автоответчик распознаётся и расходует попытку; лимит 3 линий с расчётом ёмкости в секундах и честным 429; персистентная очередь, переживающая рестарт; подписанные вебхуки at-least-once с `delivery_log` и `GET /result` как фолбэк; загрузка WAV напрямую в хранилище заказчика по presigned PUT; TTL 7 суток и `410 gone`; телефонная деградация, фоны локаций (CC0), голос/темп/тон параметрами заказа. В логах ни номеров, ни текстов реплик.

Спецификация интерфейса v1.2 прошла внешнее ревью (24 правки, 3 P0) и закалку через FPF (12 P0); 5 противоречий разрешены по ТРИЗ. Перечень зависимостей с лицензиями прикладывается к каждой сдаче.
`Python` `FastAPI` `OpenAI Realtime` `Twilio` `asyncio` `webhooks` `GRACE 4` `FPF` `ТРИЗ`

### Прогноз финансовых временных рядов на Chronos-2 | *(private, NDA)*
Недельное переобучение foundation-модели с нуля на каждую отсечку: свой датасет, своя модель, прогноз только своей недели. 7 модулей (`calendar`, `raw_store`, `dataset`, `trainer`, `forecaster`, `loader`, `run`), каждый возвращает отчёт с проверкой, а не данные. Боевой прогон на 16 отсечках, dry-run, продолжение после сбоя. ClickHouse как хранилище свечей и прогнозов, GPU в контейнере, история 5 лет, два таймфрейма.

Две закрытые утечки: старый конвейер переписывал границу обучения и сделал все 18 наборов одинаковыми (9 часов GPU впустую при красивых метриках); калибратор брал показатели с бара, которого модель не видела (+20 пунктов из будущего). Режим «без дообучения» для честного сравнения с чистым Chronos. Петля пересмотра выводов после каждого ретрейна.
`Python` `AutoGluon` `Chronos-2` `ClickHouse` `GPU` `GRACE 4`

### [Fluffy Fox Ear](https://foxear.ru) *(private repo)*
Корпоративный SaaS для транскрибации защит диссертаций. Полный цикл: загрузка аудио, очередь на Celery + Redis, транскрибация WhisperX, диаризация спикеров, генерация протоколов, биллинг ЮKassa.
`Python` `TypeScript` `Celery` `Redis` `WhisperX` `Docker`

### DefectMaster Bot - [stroycontrolbot.ru](https://stroycontrolbot.ru) | [stroycontrolai.ru](https://stroycontrolai.ru) | *(private repo)*
Telegram-бот для автоматического выявления строительных дефектов по фото. AI-анализ через Google Gemini с привязкой к нормам РФ (СНиП, ГОСТ, СП). Автогенерация отчётов в Google Таблицы. Встроенная система балансов и оплата через Tinkoff.
- **stroycontrolbot.ru** - для физических лиц
- **stroycontrolai.ru** - для юридических лиц

`Python` `aiogram` `Google Gemini` `Google Sheets API` `Tinkoff API`

### FABLE - Scan-to-BIM конвейер | *(private repo)*
Облако точек лазерного скана (E57, Leica RTC360, паспортная точность 1,9 мм на 10 м) → обмерная модель IFC (Archicad/Revit) + план DXF + карты отклонений поверхностей 25×25 мм + расчёт черновой отделки со сметой (PDF). Робастный модовый фит эталонных плоскостей (ортогональная регрессия, устойчивая к мебели), экономический оптимум штукатурки и стяжки (срубка бугров против объёма смеси), покрытие данными как first-class (измерено/частично/тень сканера), детекция посторонних объектов, регрессия 11 метрик на эталонных сканах. Полный прогон 1.8 мин. Вокруг конвейера - мини-CRM: заявки с лендинга, письмо клиенту по кнопке в Telegram, календарь выездов, мультичат для сотрудников с белым списком.
`Python` `Open3D` `NumPy/SciPy` `ifcopenshell` `ezdxf` `matplotlib` `aiogram`

### [Штаб](https://protokolov.net) - Система управления строительными совещаниями | *(private repo)*
SaaS для цифровизации протокола строительного штаба с AI-слоем. Автоматическое формирование протоколов совещаний, контроль поручений, отслеживание сроков исполнения. Интеграция с процессами стройки.
`Python` `FastAPI` `Docker` `AI` `PostgreSQL`

### idea-collection - база механизмов с RAG и MCP | *(private repo)*
2477 карточек из 30 источников (теория игр, mechanism design, стратагемы, Талеб), 26 книг разобраны LLM-агентами в конспекты. Свой RAG-стор: SQLite-индекс, поиск по описанию ситуации. MCP-сервер на 5 инструментов (`mech_search`, `mech_card`, `mech_related`, `mech_for_triz`, `mech_random`). Граф связей 279 проверенных рёбер. Карта ТРИЗ: 40 приёмов + 204 поисковых термина, 4 источника слиты. Диверсионный разбор ядра: 284 атаки с контрмерами, 146 усилений. Ведётся по GRACE 4 автономными AFK-сессиями, системный FPF-аудит.
`Python 3.12` `SQLite` `RAG` `MCP` `GRACE 4` `FPF` `ТРИЗ`

### [vacancy.teamplan.ru](https://vacancy.teamplan.ru) - MVP «Ввод вакансии через AI-помощника» | *(private repo)*
Full-stack MVP для рекрутингового стартапа. Руководитель в чате описывает позицию голосом или текстом - AI собирает структурированную вакансию с разделами (требования, обязанности, условия), задачи на интервью и чек-листы. 3-зонный UI: список вакансий ⇆ чат с AI ⇆ панель артефакта с inline-edit и real-time обновлениями через SSE.

**Backend**: Python 3.12 + FastAPI + SQLAlchemy 2.x async + Alembic + arq + Redis + Instructor + OpenRouter. Async-воркеры для генерации артефактов, полное логирование.

**Frontend**: Next.js 15 + App Router + TypeScript + AI SDK Vercel + TanStack Query + Zustand + shadcn/ui. Voice-input с live VU-meter, inline-edit полей артефакта, SSE для real-time обновлений из бэкенда.

**Workflow**: полный цикл разработки по фреймворку GRACE - requirements, knowledge-graph, technology, development-plan, verification-plan, design-doc 2500+ строк как обязательный input.

`Python 3.12` `FastAPI` `SQLAlchemy 2 async` `Next.js 15` `TypeScript` `AI SDK Vercel` `OpenRouter` `arq` `Redis` `Zustand` `shadcn/ui` `GRACE` `SSE`

### Risk Graph - AI-first управление строительными рисками | *(private repo)*
Knowledge graph на Neo4j + chat-интерфейс + 2D-визуализация графа рисков. AI-агент-навигатор: от запроса на естественном языке через генерацию Cypher-запроса до интерпретации результата. Векторный поиск по описаниям рисков и инцидентов, привязка к строительным нормам.
`Python` `FastAPI` `Neo4j` `Cypher` `GraphRAG` `LangChain` `vector search`

### [Loomio AI](https://loomio.teamplan.ru) - Мультиагентная экспертная среда | *(private repo)*
Экспертная среда на базе self-hosted Loomio с **тремя AI-экспертами** (Claude, Gemini, GPT). Когда человек-эксперт пишет в тред, ему по очереди отвечают три LLM, рассматривая вопрос с разных сторон. Роутинг между провайдерами, graceful degradation при отказе одного. Применяется для разработки расширенной методики анализа строительных графиков (с 31 до 100 пунктов проверки).
`Ruby` `Loomio` `Claude API` `Gemini API` `OpenAI API` `Multi-Agent AI`

### Музыкальный собеседник над Яндекс Станцией | *(private repo)*
Голосовой контур «Станция → агент → голосовой ответ». MCP-сервер `music`: пульт Станции по локальному протоколу Glagol/Ynison, лайки, поиск, `play_url` (произвольный mp3 по ссылке), `speak` (ответ своим голосом через TTS с нормализацией до −9 LUFS вместо голоса Алисы). «Уши» через навык Алисы → webhook на сервере → long-poll в агента. Режим дежурства `listen(timeout)`. Правило безопасности: по голосу только чтение и обратимое; отправка, удаление, оплата - только из чата. Найденное ограничение: Станция принимает строго MP3 44.1 kHz стерео.
`Python` `MCP` `Glagol` `Alice Skill` `OpenAI TTS` `ffmpeg`

### [Analytics Portal](http://147.45.184.55/) | [GitHub](https://github.com/Baho73/WhisperX-Audio-Pipeline)
Платформа бизнес-аналитики с двумя дашбордами:

**Call Analytics** - анализ телефонных переговоров отдела продаж. AI-скоринг качества звонков, BANT-квалификация лидов, воронка конверсии, эмоциональный анализ (модель DUSHA), рейтинг менеджеров, следование скрипту продаж, обработка возражений.
`React` `Chart.js` `BANT scoring` `emotion analysis`

**Construction Dashboard** - управление строительными проектами. EVM-анализ (CPI/SPI), диаграмма Ганта с drill-down, S-кривая освоения бюджета, мониторинг задач и ответственных.
`Chart.js` `EVM` `Gantt` `S-Curve`

**WhisperX Audio Pipeline** - бэкенд-пайплайн транскрибации: распознавание речи (WhisperX), диаризация спикеров, анализ эмоций. Обработка аудиозаписей совещаний, звонков и интервью.
> Demo: `user` / `demo2024`

`Python` `WhisperX` `speaker diarization` `emotion analysis` `FastAPI`

## Open Source / AI Tooling

### [GRACE Framework](https://github.com/Baho73/grace-marketplace-2) - Agent Skills для contract-driven AI-разработки
Открытый Claude Code плагин для AI-engineering методологии. Автор @osovv. Я contributor:
- **Hardening Pass 1** - anti-rationalization чек-листы для AI-агентов (модель проверяет свой выход против evidence-цитат до финального ответа), evidence-driven verification (валидация результатов LLM против реального состояния кода и тестов), knowledge-graph integrity validation.
- **Предложение в апстрим об обратимых эффектах** (август 2026) - поля EFFECTS и REVERT в контракте каждого модуля, автоматический инвентарь эффектов проекта. Агент знает не только что модуль делает, но и как это откатить. Статья RU + EN, проверена через FPF, обкатана на claudebar при миграции GRACE 3 → 4.

Формализация «контракт-первый» подхода: сначала MODULE_CONTRACT, потом knowledge graph, потом код. На моих рабочих задачах заметно снизило количество правок после генерации.

`Claude Code` `Agent Skills` `AI-driven development` `knowledge graphs` `contract-first`

### [claudebar](https://github.com/Baho73/claudebar) - панель для параллельных агентных сессий
Rust + Win32, always-on-top переключатель между открытыми сессиями Claude Code и редакторами. v0.4.1: индикатор входящих с иконками источников (Gmail, Яндекс, Mail.ru, Telegram, MAX), строка-родитель собирает письма вложенных проектов, письмо открывается по клику через роутер, «разобрано» = три плюса в первой строке, флаг снимает читатель. Мигрирован с GRACE 3 на GRACE 4: 8 модулей с контрактами, включая EFFECTS/REVERT, инвентарь эффектов.
`Rust` `Win32` `GRACE 4`

### MCP servers - Model Context Protocol для AI-агентов
Семейство серверов MCP для подключения LLM к мессенджерам, почте, документам и железу. Использую сам в работе с Claude Code / Claude Desktop / Codex CLI, часть опубликована.

- **[mcp-telegram](https://github.com/Baho73/mcp-telegram)** - подключение Telegram к Claude. Сообщения, медиа, реакции, опросы, scheduled messages и др. Hosted-версия: [mcp-telegram.com](https://mcp-telegram.com), QR-логин за 30 секунд. На основе GramJS / MTProto.
- **mail-mcp** *(private)* - почта над несколькими IMAP/SMTP (Gmail, Яндекс, Mail.ru, MXroute) + DirectAdmin API для управления ящиками. Тулзы `list_accounts / fetch / read_message / search / history / forget` с `requester_id` - одно письмо не отдаётся дважды. Роутер входящих раскладывает почту, Telegram и MAX по `.inbox` проектов и зажигает значок в claudebar; вложения тянутся на диск. Фоллбэк на STARTTLS, когда антивирус перехватывает 993/465.
- **mcp-omnichannel** *(private)* - единый мультиканальный хаб для AI-агентов. Один shared-daemon на персону держит все соединения, абстракция «Channel» поверх Telegram (GramJS), WhatsApp (Baileys), Email (IMAP/SMTP) и Matrix со сквозным шифрованием (matrix-bot-sdk + vodozemac). OS-level изоляция персон, hosted онбординг-портал.
- **[mcp-gdocs](https://github.com/Baho73/mcp-gdocs)** - создание и обновление Google Docs из Markdown с полным форматированием.
- **[mcp-server-matrix](https://github.com/Baho73/mcp-server-matrix)** - Matrix: чтение и отправка сообщений, управление комнатами.
- **[mcp-server-max](https://github.com/Baho73/mcp-server-max)** - мессенджер MAX. Плюс вклад в [renosaza/max-mcp](https://github.com/renosaza/max-mcp): восстановление после обновления клиента, фиксация отпечатка (иначе MAX отзывает сессию), `get_file_url` для вложений.
- **music** *(private)* - пульт Яндекс Станции, см. выше.
- **mech** *(private)* - поиск механизмов в idea-collection, см. выше.
- **planpulse-mcp** *(private)* - MCP-сервер (stdio, Python) для интеграции Claude Code с PlanPulse: DCMA-анализ календарно-сетевых моделей .mpp / .xer / .xml прямо из AI-агента.

`MCP` `TypeScript` `Python` `Rust` `GramJS` `MTProto` `Baileys` `matrix-bot-sdk` `E2EE` `IMAP/SMTP` `Claude Code integration`

## Другие проекты

### [AI DevOps Automation](https://github.com/Baho73/ai-devops-automation)
AI-агент для автоматизации DevOps-операций. Деплой за 15 сек вместо 7 мин, анализ логов за 10 сек, миграции БД за 30 сек. Агент читает скрипты и .env, подключается по SSH, управляет Docker-контейнерами.
`Python` `LLM` `Docker` `SSH` `Paramiko`

### [AeroflotSeg](https://github.com/Baho73/AeroflotSeg)
CV-пайплайн сегментации объектов на фото с использованием нейросетей PyTorch: детекция bbox, кроп, ресайз и финальная сегментация (rembg, SAM, U2-Net). Специализация на металлических объектах с бликами - подбор и сравнение моделей для сложных кейсов.
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
Система компьютерного зрения для производственной линии колёсных дисков. Детекция сварного шва в реальном времени через лазерную проекцию и YOLOv8. Определяет положение шва для точного позиционирования - отверстие под ниппель сверлится строго с противоположной стороны. Управление вращением диска: остановка при достижении нужной позиции.
`Python` `YOLOv8` `OpenCV` `computer vision` `industrial automation`

### [XL2MD](https://baho73.github.io/XL2MD/) | [GitHub](https://github.com/Baho73/XL2MD)
Конвертер таблиц Excel в Markdown. Однофайловый веб-инструмент - вставляете из Excel/Google Sheets, получаете готовую Markdown-таблицу. Без зависимостей, без сервера.
`JavaScript` `HTML` `GitHub Pages`

### [rosreestr2coord](https://github.com/Baho73/rosreestr2coord) - координаты по кадастровому номеру
Утилита: парсер сайта nspd.gov.ru, выгрузка координат земельного участка по кадастровому номеру. Для интеграции с ГИС-системами и автоматизации работы с проектной документацией.
`Python` `parser` `Росреестр`

### [tg-contact-extractor](https://github.com/Baho73/tg-contact-extractor) - LLM-extraction из Telegram-экспортов
Утилита для извлечения структурированных данных (контакты, события, темы) из текстовых экспортов Telegram-чатов через LLM. Кастомизируемые промпты под разные типы извлечения, вывод в JSON и Excel, тёмный GUI и CLI.
`Python` `LLM` `prompt engineering` `JSON` `Excel`

### [seo-generator](https://github.com/Baho73/seo-generator) - SEO Product Description Generator
Backend-сервис генерации SEO-описаний товаров. Демонстрация TypeScript-стека: NestJS + LangChain.js + Zod (валидация выхода LLM против схем) + OpenRouter для роутинга между моделями.
`TypeScript` `NestJS` `LangChain.js` `Zod` `OpenRouter`

### AudioStend - стенд распознавания аудиопотока с семантическим тегированием | *(private repo)*
Исследовательский стенд для распознавания аудиопотока в реальном времени с автоматическим семантическим тегированием. Параллельная работа Google Cloud STT и WhisperX для сравнения качества, real-time веб-визуализация распознанных тегов.
`Python` `WhisperX` `Google Cloud STT` `real-time` `web visualization`

### EcoAuth / TG_Auth - централизованная Telegram-аутентификация | *(private repo)*
Экосистема входа через Telegram для внешних приложений: Auth Hub (центральный сервис), клиентская библиотека для интеграции, CLI для управления, JWT-токены, FastAPI backend. Позволяет сторонним сервисам делегировать аутентификацию пользователей через Telegram-ботов.
`Python` `FastAPI` `JWT` `Telegram Bot API` `aiogram`

### HH_AI_Sender - AI-автоматизация откликов на hh.ru | *(private repo)*
Личный AI-инструмент для работы с hh.ru. Поиск вакансий по 28 запросам под два резюме (КСП + ML), AI-скоринг релевантности через OpenRouter, индивидуальные сопроводительные письма на основе описания вакансии (без шаблонов), отправка через API с браузерным фолбэком для тестов работодателя. Синк живых переписок раз в 15 минут, конвейер внешних анкет, учёт причин пропуска в БД.

Backend: FastAPI + SQLite + фоновые воркеры (loader / scorer / sender / chatpoll) с watchdog по heartbeat. Frontend: Vite + React + AG Grid. Pipeline черновиков: pending → ready → sent → errors / test_required.
`Python` `FastAPI` `Vite` `React` `OpenRouter` `Playwright` `SQLite` `AG Grid`

### [Belbin Role Test](https://roletest.ru) *(private repo)*
Веб-приложение для определения командных ролей по Белбину. Полноценный бэкенд с PostgreSQL, Docker-деплой.
`Python` `PostgreSQL` `Docker` `JavaScript`

## Учебные кейсы и методика

Тестовые задания ниже я довожу не до «работает», а до формата разбора: постановка, принятые решения и отвергнутые альтернативы, замер, честный список того, что не сделано. Так они становятся учебными кейсами, а не строчками в портфолио.

Что в этом массиве:
- **11 публичных репозиториев**, из них шесть - полные кейсы с измеренными цифрами. Автотесты в девяти, 370+ там, где число названо.
- **Видимая развилка вместо готового ответа.** Три стратегии поиска по документу с таблицей токенов, задержки и цены. Отказ от LLM в пользу правил с объяснением, почему эмбеддинги здесь лишние. Порог честного отказа, откалиброванный по данным и закрытый тестом.
- **Разбор собственных ошибок как материал.** В одном кейсе показано, как метрика давала 30 из 30, и почему честная цифра - 17 из 30. В другом - четыре случая, где я оказался неправ, и чем именно это поймал.
- **Сквозные приёмы**, которые повторяются от кейса к кейсу: честный отказ вместо догадки, тесты без сети на фикстурах, отдельный документ «решения и отвергнутые альтернативы», раздел «что не сделал и почему».

Методические активы:
- **Гайд «От чата к агентам»** для непрограммистов: ~22 000 слов, 10 практических рецептов формата «постановка, промпт, грабли, чем проверить», 8 разборов агентных оболочек (Claude Code, Codex CLI, Gemini CLI, Cline и другие), полигон с синтетическими данными и эталонными ответами. Безопасность стоит первым шагом, до установки чего-либо. Собирается в один документ скриптом, публикуется по постоянной ссылке, обратная связь через комментарии читателей.
- **Конвейер подготовки учебных материалов**: исследование → проектирование от результата → три независимые проверки (композиция, противоречия по ТРИЗ, переобещание). Каждый этап атакует результат предыдущего, а не дополняет его. Улов на одном комплекте: 10 дефектов композиции, 5 решений из противоречий, 12 мест, где заявление было сильнее доказательства.
- **Методические ответы наставника** ([test-07-11](https://github.com/Baho73/test-07-11)): почему RAG сыпется на живых вопросах и как мерить retrieval и generation раздельно; разбор кода студента по семи пунктам; план на две-три недели для застрявшего.
- Автор учебных кейсов и ревьюер в образовательных AI-проектах (под NDA). Loomio AI применяется для методической работы с ~100 экспертами. В idea-collection - полка для авторов курсов на 152 карточки.

## Тестовые задания

### [annual-report-qa](https://github.com/Baho73/annual-report-qa) - AI-ассистент по годовому отчёту компании
Тестовое Senior AI/ML: вопросы-ответы по PDF на 201 страницу с провенансом до номера страницы. Числа извлечены двумя независимыми путями (парсер + vision-модель) и сверены. Три режима поиска - полный контекст, роутер по разделам, BM25 - замерены на общем наборе вопросов: цена ответа от $2.11 до $0.31 при том же качестве. Инвестрекомендации не выдаются, ответ без источника не считается ответом. Streamlit-демо одной командой.
`Python` `RAG` `BM25` `vision` `Streamlit` `provenance`

### [crown-test-rag](https://github.com/Baho73/crown-test-rag) - RAG с цитированием и честным отказом
Тестовое Crown (AI & Data): FastAPI, эмбеддинги E5-small (`passage:`/`query:`), FAISS с персистентностью на диск, OpenRouter. Чанкование по абзацам с перекрытием, эндпоинты `/documents` и `/ask`. Порог релевантности: ниже порога LLM не вызывается, сервис отвечает «в базе знаний ответа нет». Тесты на чанкование, FAISS-поиск и контракт отказа. MIT.
`Python` `FastAPI` `E5` `FAISS` `OpenRouter` `pytest`

### [db-sanitizer](https://github.com/Baho73/db-sanitizer) - санитизация PostgreSQL-баз
Тестовое РУСАЛ: обезличивание баз перед передачей наружу. LLM строит план санитизации по метаданным схемы, не видя данных; исполняет план детерминированный движок (Greenmask). У нейросети нет доступа к содержимому, у исполнителя нет свободы импровизации.
`Python` `PostgreSQL` `Greenmask` `LLM planning`

### [position-matcher](https://github.com/Baho73/position-matcher) - нормализация должностей из 1С
Тестовое МСТРОЙ: сырые названия должностей → классификатор из 56 канонических. Только стандартная библиотека Python 3.10+, без внешних API (закрытый контур). Три шага: нормализация (регистр, ё→е, разряды, пометки «осн./совм.»), доменные синонимы, fuzzy-скоринг. 100% на размеченной выборке (50/50); 300 записей → 280 сопоставлено, 20 без соответствия, 5 (1,7%) на ручную проверку.
`Python` `stdlib` `fuzzy matching`

### [actflow](https://github.com/Baho73/actflow) - учёт оплат, проектов и закрывающих документов
Тестовое fullstack: FastAPI + React + PostgreSQL. Разбор банковской выписки, статусы актов, дашборд.
`Python` `FastAPI` `React` `PostgreSQL`

### [vibecheck](https://github.com/Baho73/vibecheck) - контроль запросов к Agent API
Тестовое: проверка запросов к Agent API «Вайб-Маркетолог» по их же каталогу - до отправки и до списания денег.
`Python` `validation`

### [test-07-11](https://github.com/Baho73/test-07-11) - наставник курса «ИИ-инженер»
Тестовое на позицию наставника: 6 заданий с ответами.

### [splitmate](https://github.com/Baho73/splitmate) - учёт совместных расходов группы
Тестовое задание: группа ведёт общие траты, сервис считает кто кому сколько должен и предлагает минимальный набор переводов для взаиморасчёта. FastAPI backend, React frontend, PostgreSQL, всё в Docker, запуск одной командой (`docker compose up`).
`Python` `FastAPI` `React` `PostgreSQL` `Docker`

### [cbr-currency-toolkit](https://github.com/Baho73/cbr-currency-toolkit) - утилиты курсов валют ЦБ РФ
Тестовое задание из трёх частей в одном репозитории (полный цикл за один заход):

1. **FastAPI веб-конвертер валют** - асинхронный HTTP-клиент с retry, TTL-кэш, кросс-конвертация через рубль с учётом номинала. Развёрнут: [converter.teamplan.ru](https://converter.teamplan.ru).
2. **Async CLI-аналитик** - обработка данных ЦБ РФ (суточная динамика, топ движений, агрегаты), экспорт в CSV/JSON, Dockerfile, requirements.txt, инструкция по запуску.
3. **Google Apps Script** - выгрузка курсов в Google Таблицу по триггеру через UrlFetchApp, обработка ошибок, запись статуса в отдельную колонку.

`Python` `FastAPI` `async` `Docker` `Google Apps Script`

### [fullstack-test-task](https://github.com/Baho73/fullstack-test-task) - File Exchange MVP
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
