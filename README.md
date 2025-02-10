## Задание 1

Опишите не менее семи таблиц, из которых состоит база данных:

- какие данные хранятся в этих таблицах;
- какой тип данных у столбцов в этих таблицах, если данные хранятся в PostgreSQL.
Приведите решение к следующему виду:

Сотрудники (

- идентификатор, первичный ключ, serial,
- фамилия varchar(50),
- ...
- идентификатор структурного подразделения, внешний ключ, integer).

___

**Ответ**

Какие данные хранятся в этих таблицах :

1 ФИО  - фамилия имя отчество сотрудника 

2 ЗП  - заработная плата сотрудника

3 Должность  - занимаемая должность сотрудника

4 Тип подразделения - отдел в котором работает сотрудник

5 Дата - дата найма сотрудника

6 Адрес - адрес филиала

7 Проект - направление работы сотрудника
___

Какой тип данных у столбцов в этих таблицах, если данные хранятся в PostgreSQL.

1 ФИО  -  строковый (varchar)

2 ЗП  - числовой (decimal/numeric)

3 Должность  - строковый (varchar)

4 Тип подразделения - строковый (varchar)

5 Дата - дата и время (tinyint)

6 Адрес - местонахождение филиала (varchar)

7 Проект - строковый (varchar)

___

Решение: 


staff (

 staff_id primary_key,

 FName VARCHAR(50) ,
 
 PName VARCHAR(50) ,
 
 SName VARCHAR(50) ,
 
 divisions_id varchar(50),
 
 Structura_id varchar(50),
 
 date_off_id datetime,
 
 position_id varchar(50),
 
 salary_id numeric,
 
 address_id VARCHAR(50),
 
 project_id VARCHAR(50),
 
)

salary (

salary_id primary_key

pay numeric

)

position (

position_id primary_key

spethion_type

)

divisions (

divisions_id primary_key

department varchar(50)

Unit Group varchar(50)

Unit Group_type

department_type

)

Structura (

Structura_id primary_key

Group varchar(50)

Structura_type 

Structura_title

)


date_off_Employee (

date_off_id primary_key

date datetime

(


branch address (

address_id primary_key

edge VARCHAR(50)

city VARCHAR(50)

street VARCHAR(50)

house VARCHAR(50)

)

project (

project_id primary_key

project_type

)

##ПРАВКА:

CREATE TABLE Адрес (
    ID INT PRIMARY KEY,
    Адрес VARCHAR(220)
);

CREATE TABLE Структурное_подразделение (
    ID INT PRIMARY KEY,
    Наименование_структурного_подразделения VARCHAR(120),
    Адрес INT,
    FOREIGN KEY (Адрес) REFERENCES Адрес(ID)
);

CREATE TABLE Дата_найма (
    ID INT PRIMARY KEY,
    Дата DATE
);

CREATE TABLE Оклад (
    ID INT PRIMARY KEY,
    Размер_оклада FLOAT
);

CREATE TABLE Должность (
    ID INT PRIMARY KEY,
    Наименование_должности VARCHAR(50)
);

CREATE TABLE Проекты (
    ID INT PRIMARY KEY,
    Наименование_проекта VARCHAR(220)
);

CREATE TABLE Сотрудники (
    ID INT PRIMARY KEY,
    Фамилия VARCHAR(50),
    Имя VARCHAR(50),
    Отчество VARCHAR(50),
    Оклад INT,
    Должность INT,
    Дата_найма INT,
    Структурное_подразделение INT,
    Проект INT,
    FOREIGN KEY (Оклад) REFERENCES Оклад(ID),
    FOREIGN KEY (Должность) REFERENCES Должность(ID),
    FOREIGN KEY (Дата_найма) REFERENCES Дата_найма(ID),
    FOREIGN KEY (Структурное_подразделение) REFERENCES Структурное_подразделение(ID),
    FOREIGN KEY (Проект) REFERENCES Проекты(ID)
);
