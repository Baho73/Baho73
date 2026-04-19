[🇬🇧 English version](README.en.md)

> **Два взгляда на один профиль:**
> **Архитектор / Product Manager** *(вы здесь)* | [Разработчик](README_developer.md)

# Ivan Ponomarev

20+ лет в строительной отрасли в роли РП, PMO и планировщика. Строю AI-продукты, которые решают реальные проблемы стройки - от ведения протоколов штабов и распределения командных ролей до аудита расписаний и контроля дефектов.

## Что я делаю

Проектирую и вывожу в продакшен AI-системы для строительной отрасли. Не как подрядчик со стороны IT, а как человек, который 20 лет составлял КСГ, ходил на штабы и координировал подрядчиков - и понимает, где болит.

6 продуктов в продакшене. 11 AI-агентов для реальных клиентов. Полный цикл: от формулировки задачи до работающего корпоративного сервиса или SaaS с биллингом.

---

## Продукты

### [PlanPulse](https://planpulse.ru) - автоматический аудит строительных расписаний
Руководитель проекта загружает график - через 30 секунд получает заключение: где проблемы, что доработать, насколько график реалистичен. Без опыта в КСП.

- Парсинг **30+ форматов** расписаний (Primavera P6, MS Project, Asta Powerproject) через MPXJ
- **31 проверка** по стандартам DCMA-14 и авторской методике PRIM_X
- AI-пояснения к каждой проверке на понятном языке
- Три интерфейса: Telegram-бот, Web App, REST API
- Микросервисная архитектура: 8 Docker-контейнеров, FastAPI, CI/CD, биллинг ЮKassa

`planpulse.ru` | [Telegram Bot](https://t.me/PrimaX_wbs_bot) | [Web App](https://planpulse.ru/app/)

### DefectMaster - AI-анализ строительных дефектов
Инспектор фотографирует дефект - бот определяет тип, оценивает критичность и указывает, какой СНиП, ГОСТ или СП нарушен. Автоматическая генерация отчёта.

- AI-анализ изображений через Google Gemini (Vision)
- Привязка к нормативной базе РФ - не абстрактное описание, а конкретная норма
- Два продукта: [stroycontrolbot.ru](https://stroycontrolbot.ru) (B2C) и [stroycontrolai.ru](https://stroycontrolai.ru) (B2B)

### [Штаб](https://protokolov.net) - цифровизация строительных совещаний
Каждую неделю на стройке - штаб. Десятки поручений, сроки, ответственные. Протоколы ведутся в Word или Excel, рассылаются по почте и теряются. «Штаб» решает это:

- Импорт существующих протоколов, формирование пунктов с голоса
- AI-помощь с формулировками и созданием чек-листов
- Контроль исполнения поручений, напоминания исполнителям
- Первичный анализ и обратная связь по предоставленным отчётам
- Уведомления по email и Telegram-бот
- Дашборд с аналитикой, отслеживание сроков

### [Loomio AI](https://teamplan.ru) - мультиагентная экспертная среда
Три LLM-эксперта (Claude, Gemini, GPT) по очереди отвечают человеку-эксперту в треде. Каждый рассматривает вопрос с разных сторон. Создан и применяется для разработки расширенной методики анализа строительных графиков с участием ~100 экспертов.

### [Belbin Role Test](https://roletest.ru) - анализ командных ролей
Инструмент, который я использовал как РП для формирования проектных команд. Психометрический анализ по методике Белбина: определяет роль каждого участника, показывает баланс команды и подсказывает, кого не хватает. Помогает при подборе новых участников и перераспределении ответственности. И поскольку этим проектом помимо суровых РП пользуются HR - там есть котики!

### [Fluffy Fox Ear](https://foxear.ru) - транскрибация и протоколирование
Корпоративный SaaS: загрузка аудиозаписей совещаний и защит, транскрибация (WhisperX), диаризация спикеров, генерация структурированных протоколов. Работа с несколькими микрофонами для выбора лучшей записи, анализ транскрибации с учётом контекста - например, текста диссертации или автореферата. Эта разработка также применена в проекте [Штаб](https://protokolov.net)

---

## AI-агенты в продакшене

11 агентов на базе LLM для автоматизации продаж, консультаций и клиентской поддержки. Каждый - не шаблонный чат-бот, а система с RAG, интеграциями и пониманием предметной области.

| Агент | Сфера | Задача |
|-------|-------|--------|
| [Цифриум](https://t.me/mvp_cifrium_bot) | EdTech | Подбор программ обучения, выявление потребностей |
| [Промышленный Университет](https://t.me/DPO_Poly_bot) | ДПО | Консультация по программам, назначение ZOOM-встреч |
| [Московский Политех](https://t.me/Politeh_FAQ_test_v2_bot) | Образование | Консультант по зачислению |
| [CruClub](https://t.me/cruclub_test_bot) | Туризм | Консультант по морским круизам |
| [Застройщик](https://t.me/Developer_consultant_bot) | Строительство | Юридическая помощь по организации строительства |
| [Евраз PM](https://t.me/evraz_pm_bot) | Корп. обучение | Помощник по управлению проектами |
| R-Vision | Кибербезопасность | Экспертная поддержка по системе R-Vision |
| [Лакокрасочный завод](https://t.me/Paint_test_sales_bot) | Производство | Менеджер по продаже ЛКМ |
| Контент-менеджер | Маркетинг | Контент-планы, анализ трендов |
| [Автоломбард](https://t.me/autolombars_bot) | Финансы | Виртуальный консультант |
| [Видеонаблюдение](https://t.me/b0095_cam_bot) | Безопасность | Подбор систем, подготовка КП |

---

## Open-Source и инструменты для AI-агентов

### MCP-серверы (Model Context Protocol)

Инфраструктура для агентов по стандарту Anthropic MCP: серверы, дающие LLM прямой доступ к корпоративным системам.

- [mcp-gdocs](https://github.com/Baho73/mcp-gdocs) - создание Google Docs из Markdown с полным форматированием (заголовки, таблицы, списки, bold/italic)
- [mcp-server-max](https://github.com/Baho73/mcp-server-max) - Max/VK Teams: отправка и чтение сообщений, управление чатами
- [mcp-server-matrix](https://github.com/Baho73/mcp-server-matrix) - Matrix-мессенджер: комнаты, сообщения, присутствие

### GRACE Framework (contributor)

[grace-marketplace](https://github.com/osovv/grace-marketplace) - open-source Claude Code plugin для контрактно-ориентированной агентной разработки. Автор [@osovv](https://github.com/osovv). Веду fork с Hardening Pass 1: разметка всех 13 skills anti-rationalization таблицами, evidence-driven verification чек-листы, усиление 5 ключевых skills (grace-fix, grace-reviewer, grace-multiagent-execute, grace-plan, grace-ask).

**Roadmap:**
- **grace-evolve** - autonomous evolutionary search, вдохновлён DeepMind FunSearch / AlphaEvolve и Sakana AI Scientist. Budget control, isolated git worktrees, archive результатов
- **grace-afk** - unattended long-running agent harness с budget control, Telegram escalation для one-way-door решений, adaptive checkpoint cadence

---

## Другие проекты

### [Analytics Portal](http://147.45.184.55/) | [GitHub](https://github.com/Baho73/WhisperX-Audio-Pipeline)
Платформа бизнес-аналитики: AI-скоринг звонков (BANT-квалификация, эмоциональный анализ DUSHA, рейтинг менеджеров) + строительный дашборд (EVM-анализ CPI/SPI, диаграмма Ганта, S-кривая бюджета).
> Demo: `user` / `demo2024`

### Weld Seam Detection | [Demo](https://youtu.be/ie_D0QS-dDo)
Computer Vision на производственной линии колёсных дисков. YOLOv8 находит сварной шов в реальном времени через лазерную проекцию и управляет остановкой вращения для точного позиционирования.

### [AI DevOps Automation](https://github.com/Baho73/ai-devops-automation)
AI-агент для автоматизации деплоя: 15 секунд вместо 7 минут. Анализ логов, миграции БД, управление Docker-контейнерами по SSH.

### [AeroflotSeg](https://github.com/Baho73/AeroflotSeg)
CV-пайплайн сегментации объектов (PyTorch, SAM, U2-Net). Специализация на металлических объектах с бликами.

### [Cluster Optimization](https://github.com/Baho73/cluster-optimization)
Кластеризация 45K текстовых эмбеддингов. Очистка ансамблем (KNN, LOF, Isolation Forest), подбор k четырьмя метриками, KMeans + t-SNE.

### [Trebuchet Simulator](https://github.com/Baho73/trebuchet-simulator)
Физический симулятор: лагранжева механика, символьный вывод уравнений (SymPy), оптимизация генетическим алгоритмом. Дальность 2 840 м.

### [XL2MD](https://baho73.github.io/XL2MD/) | [GitHub](https://github.com/Baho73/XL2MD)
Конвертер Excel -> Markdown. Однофайловый инструмент без зависимостей.

### [tg-contact-extractor](https://github.com/Baho73/tg-contact-extractor)
Извлечение структурированных данных из Telegram-экспортов через LLM с настраиваемыми промптами. Применимо к чатам поддержки, CRM-миграциям, аналитике переписки.

### [seo-generator](https://github.com/Baho73/seo-generator)
SEO-генератор описаний товаров: NestJS + LangChain.js + Zod + OpenRouter. Типизированный пайплайн с валидацией схем через Zod - пример работы с LLM в Node.js/TypeScript-экосистеме.

---

## Стек

**Backend:** Python, FastAPI, Docker, PostgreSQL, CI/CD

**Node.js / TypeScript:** NestJS, LangChain.js, Zod

**AI/ML:** PyTorch, scikit-learn, YOLOv8, OpenCV, LangChain, FAISS, WhisperX

**LLM:** OpenAI, Claude, Gemini API, RAG, prompt engineering, multi-agent systems

**Agent infrastructure:** MCP (Model Context Protocol), Claude Code skills, OpenRouter

**Строительные стандарты:** DCMA-14, PRIM_X, EVM (CPI/SPI), критический путь, Primavera P6, MS Project, Spider Project

---

## Контакты

[![Telegram](https://img.shields.io/badge/Telegram-@IvanPonomarev-blue?logo=telegram)](https://t.me/IvanPonomarev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-ivanponomarev-blue?logo=linkedin)](https://linkedin.com/in/ivanponomarev)
