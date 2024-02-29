# Домашнее задание к занятию "`Индексы`" - `Рамазанов Бакит`


Задание можно выполнить как в любом IDE, так и в командной строке.

### Задание 1

Напишите запрос к учебной базе данных, который вернёт процентное отношение общего размера всех индексов к общему размеру всех таблиц.

```
SELECT table_schema as DB_name
	,CONCAT(ROUND((SUM(index_length))*100/(SUM(data_length+index_length)),2),'%') '% of index'
FROM information_schema.TABLES where TABLE_SCHEMA = 'sakila'
```



### Задание 2

Выполните explain analyze следующего запроса:
```sql
select distinct concat(c.last_name, ' ', c.first_name), sum(p.amount) over (partition by c.customer_id, f.title)
from payment p, rental r, customer c, inventory i, film f
where date(p.payment_date) = '2005-07-30' and p.payment_date = r.rental_date and r.customer_id = c.customer_id and i.inventory_id = r.inventory_id
```
- перечислите узкие места;
- оптимизируйте запрос: внесите корректировки по использованию операторов, при необходимости добавьте индексы.

решение:
```
EXPLAIN ANALYZE
SELECT DISTINCT CONCAT(c.last_name, ' ', c.first_name), 
       SUM(p.amount) OVER (PARTITION BY c.customer_id)
FROM payment p
JOIN customer c ON p.customer_id = c.customer_id
WHERE DATE(p.payment_date) = '2005-07-30';
```

Изменения и оптимизации:

Лишние таблицы и столбцы: Убраны ненужные таблицы rental, inventory, и film, так как данные из них не используются.

Индексы: Убедитесь, что у столбца payment.payment_date и customer.customer_id существуют индексы для улучшения производительности.

Условие для оконной функции: Убрана часть условия из PARTITION BY, так как вам нужна сумма по customer_id, а film.title больше не используется.


Добработка
```
EXPLAIN ANALYZE
SELECT CONCAT(c.last_name, ' ', c.first_name) AS customer_name, 
       SUM(p.amount) OVER (PARTITION BY c.customer_id) AS total_amount
FROM payment p
JOIN customer c ON p.customer_id = c.customer_id
WHERE p.payment_date >= '2005-07-30' AND p.payment_date < DATE_ADD('2005-07-30', INTERVAL 1 DAY);
```
