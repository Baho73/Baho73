# Ivan Ponomarev

Python-разработчик. Строю AI-продукты: от идеи до работающего сервиса на проде.

## Стек

**Основное:** Python, TypeScript, SQL (PostgreSQL, SQLite, MySQL)

**Data Science:** pandas, numpy, matplotlib, Jupyter, обработка и анализ данных

**AI/ML:** PyTorch, TensorFlow, SKLearn, YOLOv8, Google Gemini, WhisperX, speaker diarization, emotion analysis, computer vision

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

### [Analytics Portal](http://147.45.184.55/) | [GitHub](https://github.com/Baho73/WhisperX-Audio-Pipeline)
Платформа бизнес-аналитики с двумя дашбордами:

**Call Analytics** — анализ телефонных переговоров отдела продаж. AI-скоринг качества звонков, BANT-квалификация лидов, воронка конверсии, эмоциональный анализ (модель DUSHA), рейтинг менеджеров, следование скрипту продаж, обработка возражений.
`React` `Chart.js` `BANT scoring` `emotion analysis`

**Construction Dashboard** — управление строительными проектами. EVM-анализ (CPI/SPI), диаграмма Ганта с drill-down, S-кривая освоения бюджета, мониторинг задач и ответственных.
`Chart.js` `EVM` `Gantt` `S-Curve`

**WhisperX Audio Pipeline** — бэкенд-пайплайн транскрибации: распознавание речи (WhisperX), диаризация спикеров, анализ эмоций. Обработка аудиозаписей совещаний, звонков и интервью.
> Demo: `user` / `demo2024`

`Python` `WhisperX` `speaker diarization` `emotion analysis` `FastAPI`

### [AI DevOps Automation](https://github.com/Baho73/ai-devops-automation)
AI-агент для автоматизации DevOps-операций. Деплой за 15 сек вместо 7 мин, анализ логов за 10 сек, миграции БД за 30 сек. Агент читает скрипты и .env, подключается по SSH, управляет Docker-контейнерами.
`Python` `LLM` `Docker` `SSH` `Paramiko`

### [AeroflotSeg](https://github.com/Baho73/AeroflotSeg)
CV-пайплайн сегментации объектов на фото с использованием нейросетей PyTorch: детекция bbox, кроп, ресайз и финальная сегментация (rembg, SAM, U2-Net). Специализация на металлических объектах с бликами — подбор и сравнение моделей для сложных кейсов.
`Python` `PyTorch` `OpenCV` `SAM` `U2-Net` `computer vision`

### [Cluster Optimization](https://github.com/Baho73/cluster-optimization)
Полный DS-пайплайн кластеризации 45K текстовых эмбеддингов. Очистка данных ансамблем из 3 методов (KNN, LOF, Isolation Forest), подбор оптимального k четырьмя метриками (Elbow, Silhouette, Calinski-Harabasz, Davies-Bouldin), финальная кластеризация KMeans + t-SNE визуализация.
`Python` `scikit-learn` `pandas` `matplotlib` `t-SNE` `KMeans`

### Weld Seam Detection | [Demo](https://youtu.be/ie_D0QS-dDo)
Система компьютерного зрения для производственной линии колёсных дисков. Детекция сварного шва в реальном времени через лазерную проекцию и YOLOv8. Определяет положение шва для точного позиционирования — отверстие под ниппель сверлится строго с противоположной стороны. Управление вращением диска: остановка при достижении нужной позиции.
`Python` `YOLOv8` `OpenCV` `computer vision` `industrial automation`

### [Belbin Role Test](https://roletest.ru)
Веб-приложение для определения командных ролей по Белбину. Полноценный бэкенд с PostgreSQL, Docker-деплой.
`Python` `PostgreSQL` `Docker` `JavaScript`

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
