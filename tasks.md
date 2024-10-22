# Tasks

### task-01 
Напишіть SQL-запит, який для таблиці `orders` з атрибута `date` витягує рік, місяць і число. Виведіть на екран їх у три окремі атрибути поряд з атрибутом `id` та оригінальним атрибутом `date` (всього вийде 5 атрибутів).

```sql
USE test_db;

SELECT 
    id,
    date,
    YEAR(date) AS year,
    MONTH(date) AS month,
    DAY(date) AS day
FROM
    orders;
```
Результат виконання:

![ResultOfExecution](img/p1_date.png)

### task-02 
Напишіть SQL-запит, який для таблиці `orders` до атрибута `date` додає один день. На екран виведіть атрибут `id`, оригінальний атрибут `date` та результат додавання.

```sql
SELECT id, date, date + INTERVAL 1 DAY FROM orders;
```

Результат виконання:

![ResultOfExecution](img/p2_interval.png)

### task-03
Напишіть SQL-запит, який для таблиці `orders` для атрибута `date` відображає кількість секунд з початку відліку (показує його значення timestamp). Для цього потрібно знайти та застосувати необхідну функцію. На екран виведіть атрибут `id`, оригінальний атрибут `date` та результат роботи функції.

```sql
SELECT id, date, UNIX_TIMESTAMP(date) FROM orders;
```

Результат виконання:

![ResultOfExecution](img/p3_unix_timestamp.png)

### task-04 
Напишіть SQL-запит, який рахує, скільки таблиця `orders` містить рядків з атрибутом `date` у межах між `1996-07-10 00:00:00` та `1996-10-08 00:00:00`.

```sql
SELECT 
    COUNT(*) AS count_interval
FROM
    orders
WHERE
    date >= '1996-07-10 00:00:00'
        AND date <= '1996-10-08 00:00:00';
```

Результат виконання:

![ResultOfExecution](img/p4_dates_in_range.png)

### task-05 
Напишіть SQL-запит, який для таблиці `orders` виводить на екран атрибут `id`, атрибут `date` та JSON-об’єкт `{"id": <атрибут id рядка>, "date": <атрибут date рядка>}`. Для створення JSON-об’єкта використайте функцію.

```sql
SELECT 
    id,
    date,
    JSON_OBJECT('id', id, 'date', date) AS data_to_json
FROM
    orders;
```

Результат виконання:

![ResultOfExecution](img/p5_json_object.png)
