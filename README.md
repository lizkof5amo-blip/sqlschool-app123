# SQL Middle+ Trainer v0.2

Учебный сервис по PostgreSQL для системного аналитика. SQL выполняется в PGlite — PostgreSQL/WASM прямо в браузере. VPS и локальная установка PostgreSQL не требуются.

## Что работает

- 40-урочный roadmap Base → Middle+ → Interview → Capstone.
- Уроки 1–8 наполнены расширенной теорией и 69 автопроверяемыми задачами.
- Единая CRM-модель: users, companies, contacts, pipelines, stages, deals, tasks, products, deal_products.
- PostgreSQL-песочница в браузере с сохранением БД в IndexedDB.
- Автопроверка SELECT/DDL/DML на чистой копии seed-базы.
- Локальный прогресс и журнал всех попыток.
- Диагностика слабых тем по ошибкам.
- Interview mode с вопросами по всем 40 урокам.
- Экспорт progress JSON и копирование отчёта для разбора в ChatGPT.
- Уроки 1 и 2 по умолчанию отмечены как пройденные — перенесено из текущего обучения.

## Запуск локально

Из папки проекта:

```bash
python3 -m http.server 8080
```

Открыть http://localhost:8080

`file://` не подходит, потому что используются ES modules.

## Деплой на Vercel

Проект статический. Build command не нужен. Output directory — корень проекта.

PGlite загружается из официально рекомендуемого browser CDN jsDelivr. При первом открытии нужен интернет.

## Архитектура

Browser UI → PGlite/PostgreSQL WASM → IndexedDB

Progress → localStorage

Следующий слой:
- Supabase Auth;
- синхронизация progress/attempts;
- course content в Supabase;
- доступ ChatGPT к журналу через Supabase connector;
- автогенерация персональных контрольных по слабым темам.

Учебный SQL даже после подключения Supabase желательно оставлять в PGlite, чтобы `DROP TABLE`/`DELETE` ученика не затрагивал backend сервиса.
