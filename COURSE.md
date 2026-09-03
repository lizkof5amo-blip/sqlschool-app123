# SQL Middle+ — программа курса

Всего уроков: 40. Цель: уверенный SQL/PostgreSQL для системного аналитика Middle+ и подготовка к собеседованиям.

## 1. Фундамент PostgreSQL

### 1. БД, PostgreSQL и первый SELECT (Base)

Как устроена реляционная БД, чем СУБД отличается от SQL, PK/FK/NULL и логика SELECT.

**После урока:** Различать БД, СУБД и SQL; Читать таблицу как сущность/строки/атрибуты; Понимать PK, FK и NULL; Писать SELECT/FROM/WHERE.

### 2. Типы данных, ограничения и CREATE TABLE (Base)

Типы PostgreSQL, NOT NULL/UNIQUE/DEFAULT/CHECK, идентификаторы и создание таблиц.

**После урока:** Выбирать тип по семантике данных; Отличать тип данных от ограничения; Создавать таблицы; Формулировать data constraints из требований.

### 3. INSERT, UPDATE, DELETE, RETURNING и CRUD (Base+)

Изменение данных безопасно: INSERT/UPDATE/DELETE, RETURNING, опасность массовых изменений.

**После урока:** Добавлять одну и несколько строк; Изменять/удалять с WHERE; Использовать RETURNING; Понимать CRUD и риск DML без фильтра.

### 4. SELECT глубже: выражения, aliases, DISTINCT (Base+)

Формирование результата: вычисляемые поля, алиасы, DISTINCT и аккуратный SELECT.

**После урока:** Писать выражения в SELECT; Использовать AS; Понимать DISTINCT и его цену; Не злоупотреблять SELECT *.

### 5. WHERE: AND/OR/NOT, IN, BETWEEN и приоритет (Base+)

Логика фильтрации без типичных ошибок скобок и границ диапазона.

**После урока:** Строить составные predicates; Знать приоритет AND/OR; Использовать IN/BETWEEN; Корректно задавать диапазоны.

### 6. Строки: LIKE/ILIKE, функции и нормализация поиска (Base+)

Поиск по тексту, регистр, шаблоны, строковые функции и влияние на индекс.

**После урока:** Использовать LIKE/ILIKE; Понимать % и _; Применять LOWER/TRIM/CONCAT; Видеть риск несаргабельных условий.

## 2. Уверенный SELECT

### 7. NULL и трёхзначная логика (Middle core)

NULL как unknown, IS NULL, COALESCE, NULLIF и SQL three-valued logic.

**После урока:** Не сравнивать NULL через =; Понимать TRUE/FALSE/UNKNOWN; Использовать COALESCE/NULLIF; Предсказывать поведение NULL в фильтрах.

### 8. Дата, время, интервалы и часовые пояса (Middle core)

DATE/TIMESTAMP/TIMESTAMPTZ, CURRENT_TIMESTAMP, INTERVAL и стратегия UTC.

**После урока:** Различать date/time types; Фильтровать интервалы времени; Понимать UTC vs local; Не допускать off-by-one day/timezone bugs.

### 9. ORDER BY, LIMIT/OFFSET и keyset pagination (Middle core)

Стабильная сортировка, top-N и почему OFFSET деградирует на больших данных.

**После урока:** Сортировать по нескольким полям; Делать deterministic order; Использовать LIMIT/OFFSET; Понимать keyset pagination.

### 10. Агрегаты: COUNT/SUM/AVG/MIN/MAX (Middle core)

Расчёт метрик и важные различия COUNT(*), COUNT(column), NULL.

**После урока:** Считать метрики; Понимать NULL в агрегатах; Различать COUNT(*)/COUNT(col); Использовать FILTER.

### 11. GROUP BY и функциональная зависимость (Middle core)

Группировки, гранулярность результата и типичная ошибка «column must appear in GROUP BY».

**После урока:** Определять grain результата; Группировать корректно; Комбинировать агрегаты; Не терять смысл метрики.

### 12. HAVING и условная агрегация (Middle core)

Фильтрация групп после агрегации и KPI-запросы.

**После урока:** Различать WHERE/HAVING; Фильтровать группы; Строить KPI по менеджерам.

## 3. Связи и реляционные запросы

### 13. INNER JOIN: кардинальность и ключ соединения (Middle core)

Соединение таблиц без дубликатов и понимание 1:1/1:N.

**После урока:** Выбирать корректный ON; Предсказывать число строк; Видеть 1:N multiplication; Отличать JOIN condition от filter.

### 14. LEFT/RIGHT/FULL/CROSS JOIN (Middle core)

Сохранение отсутствующих связей и анти-join паттерны.

**После урока:** Использовать LEFT JOIN; Находить объекты без связей; Понимать FULL/CROSS; Не ломать LEFT JOIN фильтром в WHERE.

### 15. Many-to-many и junction tables (Middle core)

Связь сделок и товаров через deal_products с атрибутами связи.

**После урока:** Проектировать N:M; Работать с junction table; Хранить quantity/unit_price на связи.

### 16. Self JOIN и иерархии (Middle+)

Самосвязи: руководитель-сотрудник, родительская сущность и древовидные структуры.

**После урока:** Понимать self FK; Писать self JOIN; Видеть иерархические модели.

### 17. JOIN 3–6 таблиц и контроль дублей (Middle+)

Рабочие CRM-запросы через users/companies/contacts/deals/tasks.

**После урока:** Собирать multi-join; Контролировать grain; Локализовать источник дублей.

### 18. EXISTS, NOT EXISTS и semi/anti joins (Middle+)

Проверка существования без размножения строк.

**После урока:** Использовать EXISTS; Отличать EXISTS от JOIN; Строить anti-join через NOT EXISTS.

## 4. Продвинутый SQL

### 19. Подзапросы: scalar, IN и correlated (Middle+)

Вложенные запросы и корреляция.

**После урока:** Писать scalar subquery; Понимать correlated subquery; Выбирать JOIN/EXISTS/subquery.

### 20. CTE и WITH (Middle+)

Декомпозиция сложных запросов, читаемость, рекурсивный CTE обзор.

**После урока:** Разбивать запрос на этапы; Переиспользовать CTE; Понимать recursive CTE concept.

### 21. CASE и условные метрики (Middle+)

Бизнес-классификация и conditional aggregation.

**После урока:** Писать CASE; Строить buckets; Считать conversion и KPI.

### 22. UNION / UNION ALL / INTERSECT / EXCEPT (Middle+)

Операции множеств и совместимость схем.

**После урока:** Объединять наборы строк; Знать UNION vs UNION ALL; Использовать EXCEPT для сверки данных.

### 23. Оконные функции: OVER/PARTITION BY (Middle+)

Агрегаты без схлопывания строк, ROW_NUMBER/RANK.

**После урока:** Понимать window vs GROUP BY; Использовать ROW_NUMBER; Строить рейтинг внутри группы.

### 24. Продвинутые окна: LAG/LEAD и frames (Middle+)

Предыдущие значения, накопительные суммы, оконные рамки.

**После урока:** Использовать LAG/LEAD; Считать running total; Понимать ROWS/RANGE frames.

## 5. Проектирование данных

### 25. DDL: ALTER/DROP/TRUNCATE и schemas (Middle+)

Изменение структуры без потери понимания зависимостей.

**После урока:** Добавлять/переименовывать столбцы; Различать DROP/TRUNCATE/DELETE; Понимать schema namespace.

### 26. FK, CHECK, CASCADE, RESTRICT и deferrable (Middle+)

Ссылочная целостность и жизненный цикл связанных сущностей.

**После урока:** Выбирать ON DELETE strategy; Формулировать CHECK constraints; Понимать deferred validation concept.

### 27. Нормализация 1NF–3NF и аномалии (Middle core)

Практическая нормализация без академического перегруза.

**После урока:** Видеть repeating groups; Находить update/insert/delete anomalies; Декомпозировать до 3NF.

### 28. ERD, кардинальность и optionality (Middle core)

Перевод требований в сущности, атрибуты и связи.

**После урока:** Выделять сущности; Определять 1:1/1:N/N:M; Фиксировать обязательность; Выбирать ownership.

### 29. Natural vs surrogate keys, UUID и идентичность (Middle+)

Стратегия идентификаторов и интеграционные external_id.

**После урока:** Различать natural/surrogate; Понимать UUID tradeoffs; Моделировать external IDs.

## 6. Производительность и надёжность

### 30. Индексы: B-tree, composite, partial, expression (Middle+)

Как индексы ускоряют чтение и удорожают запись.

**После урока:** Понимать B-tree; Проектировать составной индекс; Знать leftmost prefix; Понимать partial/expression indexes.

### 31. EXPLAIN / EXPLAIN ANALYZE (Middle+)

Чтение планов: Seq Scan, Index Scan, joins, rows estimation.

**После урока:** Читать базовый plan; Отличать estimated/actual rows; Находить misestimation; Понимать стоимость.

### 32. Транзакции и ACID (Middle core)

Атомарность бизнес-операций, COMMIT/ROLLBACK и границы транзакции.

**После урока:** Определять transaction boundary; Использовать BEGIN/COMMIT/ROLLBACK; Понимать ACID practically.

### 33. Isolation, MVCC и аномалии конкурентности (Middle+)

Read Committed/Repeatable Read/Serializable, lost update, phantom и MVCC.

**После урока:** Объяснять isolation levels; Понимать snapshot/MVCC; Распознавать race conditions.

### 34. Locks и deadlocks (Middle+)

Row/table locks, SELECT FOR UPDATE, порядок захвата и deadlock.

**После урока:** Понимать blocking; Распознавать deadlock; Выбирать consistent lock order.

### 35. Performance anti-patterns и SARGability (Middle+)

N+1, функции на indexed column, leading wildcard, overfetch, pagination.

**После урока:** Видеть N+1; Писать sargable predicates; Уменьшать объём данных.

## 7. PostgreSQL для системного аналитика

### 36. Views, materialized views и контракт чтения (Middle+)

Представления для стабильного интерфейса данных и предрасчётов.

**После урока:** Понимать view; Знать materialized refresh; Использовать view как read contract.

### 37. JSONB, массивы и гибкие атрибуты (Middle+)

Когда JSONB уместен в PostgreSQL и когда он превращает схему в свалку.

**После урока:** Читать JSONB operators; Понимать GIN concept; Выбирать columns vs JSONB.

### 38. Миграции, data quality, dedup и soft delete (Middle+)

Безопасное изменение схемы и очистка данных в интеграциях.

**После урока:** Планировать migration sequence; Находить дубли; Понимать soft delete/audit fields; Проектировать idempotent imports.

## 8. Interview & Capstone

### 39. SQL на собеседовании системного аналитика (Interview)

Блиц по теории + задачи уровня Middle/Middle+ с устным объяснением решения.

**После урока:** Отвечать без терминологической путаницы; Комментировать tradeoffs; Решать SQL под таймер; Находить ошибки чужих запросов.

### 40. Capstone: спроектируй CRM-интеграцию end-to-end (Capstone)

Финальная работа: требования → ERD → DDL → seed → запросы → индексы → транзакции → интервью-защита.

**После урока:** Спроектировать БД из требований; Обосновать PK/FK/constraints; Написать 15+ рабочих запросов; Защитить решения и tradeoffs.
