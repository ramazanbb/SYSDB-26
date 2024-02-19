# Домашнее задание к занятию "`Базы данных`" - `Рамазанов Бакит`


### Легенда

Заказчик передал вам [файл в формате Excel](https://github.com/netology-code/sdb-homeworks/blob/main/resources/hw-12-1.xlsx), в котором сформирован отчёт. 

На основе этого отчёта нужно выполнить следующие задания.

### Задание 1

Опишите не менее семи таблиц, из которых состоит база данных:

- какие данные хранятся в этих таблицах;
- какой тип данных у столбцов в этих таблицах, если данные хранятся в PostgreSQL.

Приведите решение к следующему виду:

Сотрудники (

- идентификатор, первичный ключ, serial,
- фамилия varchar(50),
- ...
- идентификатор структурного подразделения, внешний ключ, integer).

---

### Решение 1
Какие данные хранятся в этих таблицах :

ФИО сотрудника - фамилия имя и отчество сотрудника

Оклад - заработная плата сотрудника

Должность - занимаемая должность сотрудника

Тип подразделения - структура подразделения

Структурное подразделение - навание подразделения

Дата найма - дата найма сотрудника

Адрес филиала - местонахождение филиала

Проект на который назначен - наименование проекта для конкретного сотрудника.


employees (

    id_employee SERIAL PRIMARY KEY,

    last_name VARCHAR(50) NOT NULL,
    
    first_name VARCHAR(50) NOT NULL,
    
    surname VARCHAR(50),
    
    rank_id INTEGER REFERENCES ranks(id_rank),
    
    salary_id INTEGER REFERENCES salary(id_salary),
    
    subdivision_id INTEGER REFERENCES subdivisions(id_subdivision),
    
    office_id INTEGER REFERENCES offices(id_office),
    
    project_id INTEGER REFERENCES projects(id_project),
    
    hired_since DATE NOT NULL
    
);


subdivisions (
    
    id_subdivision SERIAL PRIMARY KEY,
    
    subdivision VARCHAR(100) NOT NULL,
    
    type_of_subdivision_id INTEGER REFERENCES type_of_subdivision(id_of_type),
    
    office_id INTEGER REFERENCES offices(id_office)
);


type_of_subdivision (
    
    id_of_type SERIAL PRIMARY KEY,
    
    type VARCHAR(50) NOT NULL
);


offices (
    
    id_office SERIAL PRIMARY KEY,
    
    office VARCHAR(200) NOT NULL
);


projects (
    
    id_project SERIAL PRIMARY KEY,
    
    project VARCHAR(100) NOT NULL
);


ranks (
    id_rank SERIAL PRIMARY KEY,
    rank VARCHAR(100) NOT NULL
);



salary (
    id_salary SERIAL PRIMARY KEY,
    salary REAL NOT NULL
);

