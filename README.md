# Домашнее задание к занятию "`Базы данных, их типы`" - `Рамазанов Бакит`


### Задание 1. СУБД
### Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать 
правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для
каждой предметной области. 

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему? 
 
1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков.
СУБД должна гарантировать целостность и чёткую структуру данных.

`Для бюджетирования проектов и формирования финансовых аналитических отчетов с прогнозированием рисков рекомендуется использовать реляционные СУБД, такие как PostgreSQL, Oracle Database или Microsoft SQL Server. 
Они обеспечивают целостность данных и четкую структуру, что критично при работе с финансовой информацией.`

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к 
маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? 
СУБД должны быть гибкими и быстрыми.

`Для девелоперских проектов и CRM лучше использовать гибкие и быстрые NoSQL базы данных, например MongoDB. 
Они позволяют удобно хранить и обрабатывать разнообразные данные, характерные для лендингов и CRM.`

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу 
и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.

`Для базы по корпоративным нормам и правилам, обучающему материалу и т.д., можно использовать реляционные СУБД.`

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов 
по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать
со связями.

`Для задач логистики, связанных с формированием маршрутов и распределением курьеров, подходят графовые СУБД. 
Они позволяют эффективно работать со связями между объектами.`

*Приведите ответ в свободной форме.*

### Задание 2. Транзакции

2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы 
транзакция завершилась успешно. Ориентируйтесь на шесть действий.
``
1. Начало транзакции.
2. Указание суммы, на которую будет пополнен счёт.
3. Проверка баланса пополняемого счёта.
4. Пополнение баланса на определённую сумму.
5. Сохранение баланса полполняемого счёта.
6. Окончание транзакции.

``

*Приведите ответ в свободной форме.*

---

### Задание 3. SQL vs NoSQL
3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL. 

3.1.* Какие, на ваш взгляд, преимущества у NewSQL систем перед SQL и NoSQL.

*Приведите ответ в свободной форме.*

---

### Задание 4. Кластеры
Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу 
выделено 1000 машин. 

На основе какого критерия будете выбирать тип СУБД и какая модель *распределённых вычислений* 
здесь справится лучше всего и почему?

*Приведите ответ в свободной форме.*

---
