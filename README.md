# Домашнее задание к занятию "`SQL. Часть 1`" - `Рамазанов Бакит`


Задание можно выполнить как в любом IDE, так и в командной строке.

### Задание 1

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

```
SELECT DISTINCT district
FROM sakila.address
WHERE district LIKE 'K%a' AND district NOT LIKE '% %';
```
### Задание 2

Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года **включительно** и стоимость которых превышает 10.00.
```
SELECT payment_id, amount, payment_date
FROM sakila.payment
WHERE payment_date BETWEEN '2005-06-15' AND '2005-06-18'  AND amount > 10.00;
```
### Задание 3

Получите последние пять аренд фильмов.
```
SELECT rental_id, rental_date 
FROM rental
ORDER BY rental_date DESC
LIMIT 5;
```
### Задание 4

Одним запросом получите активных покупателей, имена которых Kelly или Willie. 

Сформируйте вывод в результат таким образом:
- все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
- замените буквы 'll' в именах на 'pp'.

```
SELECT 
  customer_id,
  LOWER(first_name) AS lower_first_name,
  LOWER(last_name) AS lower_last_name,
  REPLACE(LOWER(first_name), 'll', 'pp') AS replaced_first_name
FROM 
  sakila.customer
WHERE 
  first_name = 'Kelly' OR first_name = 'Willie';
```
