# Ivan Ponomarev

Python-разработчик. Строю AI-продукты: от идеи до работающего сервиса на проде.

## Стек

**Основное:** Python, TypeScript, SQL (PostgreSQL, SQLite, MySQL)

**AI/ML:** Google Gemini, WhisperX, speaker diarization, emotion analysis, computer vision

**RAG:** FAISS, векторные БД, embeddings, поиск по документам

**Backend:** aiogram, FastAPI, Docker, SSH-автоматизация, systemd

**Интеграции:** Telegram Bot API, Google Sheets/Drive API, Tinkoff API

**DevOps:** Docker, CI/CD, автоматизация деплоя через Python + SSH

## Проекты

### [Fluffy Fox Ear](https://foxear.ru) | [GitHub](https://github.com/Baho73/Fluffy-Fox-Ear)
Корпоративный SaaS для транскрибации защит диссертаций. Полный цикл: загрузка аудио, транскрибация, диаризация спикеров, генерация протоколов.
`Python` `TypeScript` `Docker`

### DefectMaster Bot — [stroycontrolbot.ru](https://stroycontrolbot.ru) | [stroycontrolai.ru](https://stroycontrolai.ru) | [GitHub](https://github.com/Baho73/DefectMaster-Bot)
Telegram-бот для автоматического выявления строительных дефектов по фото. AI-анализ через Google Gemini с привязкой к нормам РФ (СНиП, ГОСТ, СП). Автогенерация отчётов в Google Таблицы. Встроенная система балансов и оплата через Tinkoff.
- **stroycontrolbot.ru** — для физических лиц
- **stroycontrolai.ru** — для юридических лиц

`Python` `aiogram` `Google Gemini` `Google Sheets API` `Tinkoff API`

### [WhisperX Audio Pipeline](http://147.45.184.55/) | [GitHub](https://github.com/Baho73/WhisperX-Audio-Pipeline)
Пайплайн аудиотранскрибации: распознавание речи (WhisperX), диаризация спикеров, анализ эмоций. Готовый инструмент для обработки аудиозаписей совещаний и интервью. Включает дашборд строительной аналитики.
> Demo: `user` / `demo2024`

`Python` `WhisperX` `speaker diarization` `emotion analysis`

### [AI DevOps Automation](https://github.com/Baho73/ai-devops-automation)
Система автоматизации DevOps-операций через AI. Деплой за 15 сек вместо 7 мин, анализ логов за 10 сек, миграции БД за 30 сек. AI читает скрипты и .env, подключается по SSH, управляет Docker-контейнерами.
`Python` `Docker` `SSH` `Paramiko`

### [AeroflotSeg](https://github.com/Baho73/AeroflotSeg)
Пайплайн сегментации объектов на фото: удаление фона, детекция bbox, кроп, ресайз и финальная сегментация (rembg, SAM, U2-Net). Специализация на металлических объектах с бликами.
`Python` `OpenCV` `SAM` `U2-Net` `PyTorch`

### [Belbin Role Test](https://roletest.ru)
Веб-приложение для определения командных ролей по Белбину. Полноценный бэкенд с PostgreSQL, Docker-деплой.
`Python` `PostgreSQL` `Docker` `JavaScript`

## AI-боты: поддержка и продажи

Telegram-боты на базе LLM для автоматизации продаж, консультаций и клиентской поддержки в различных отраслях:

| Бот | Сфера | Задача |
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

`Python` `aiogram` `LLM` `Prompt Engineering` `Google Sheets API`

## Контакты

[![Telegram](https://img.shields.io/badge/Telegram-@IvanPonomarev-blue?logo=telegram)](https://t.me/IvanPonomarev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-ivanponomarev-blue?logo=linkedin)](https://linkedin.com/in/ivanponomarev)
