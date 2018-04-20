# InterviewQuestionsDotNet
Junior .NET Developer tests

## General

1.	What are your career goals (а) 3 years from now; (b) 10 years from now?
2.	What is SCRUM?

	[Scrum](https://www.visualstudio.com/learn/what-is-scrum/) is a framework used by teams to manage their work. Scrum implements the principles of [Agile](https://www.visualstudio.com/learn/what-is-agile/) as a concrete set of practices and roles. [Video](https://www.youtube.com/watch?v=8fC6azg69n4)

3.	During development of a new functionality you have found a bug in existing code. What action do you take?
4.	How do you maintain your code to prove that it is a good quality code?
5.	Who/what is QA? Do we need them in the development process?
6.	What version control systems are need for? What version control systems have you worked with?

	Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. [GIT](https://git-scm.com/book/en/v2)

7.	What is UAC?
8.	A custumer reports slow perormance of your application that was not reproduced in development environment. What would you suggest to do to find and localize the reason?

## DB/SQL

1.	Write a query that shows all clients (FIRST NAME, LAST NAME) that occur more than once in the following client table. The query should also show how often the client occurs in the table.
```
Table ClientRequests

		RequsetID   	INT(PK)
		FirstName	Varchar(255)		
		LastName 	Varchar(255)

		SELECT 	count (RequestID) CNT, FirstName, LastName  
		FROM ClientsRequests 
		group by FirstName, LastName
		having count (RequestID) > 1
```
2.	What is the difference between UNIQUE constraint and PRIMARY KEY constraint?

The UNIQUE constraint ensures that all values in a column are different. Both the UNIQUE and PRIMARY KEY constraints provide a guarantee for uniqueness for a column or set of columns. A PRIMARY KEY constraint automatically has a UNIQUE constraint. However, you can have many UNIQUE constraints per table, but only one PRIMARY KEY constraint per table.
```
	CREATE TABLE Persons (
  	  ID int NOT NULL UNIQUE,
    	LastName varchar(255) NOT NULL,
    	FirstName varchar(255),
    	Age int
	);
```
To name a UNIQUE constraint, and to define a UNIQUE constraint on multiple columns, use the following SQL syntax: 
```
	CREATE TABLE Persons (
    	ID int NOT NULL,
    	LastName varchar(255) NOT NULL,
    	FirstName varchar(255),
    	Age int,
    	CONSTRAINT UC_Person UNIQUE (ID,LastName)
	);
```
The PRIMARY KEY constraint uniquely identifies each record in a database table. Primary keys must contain UNIQUE values, and cannot contain NULL values. A table can have only one primary key, which may consist of single or multiple fields.
```	
	CREATE TABLE Persons (
    	ID int NOT NULL PRIMARY KEY,
    	LastName varchar(255) NOT NULL,
    	FirstName varchar(255),
    	Age int
	);
```
3.	You have discovered a bad performing query. Describe shortly what actions you can take to optimize it.

4.	Describe the use of the HAVING clause

[GROUP and HAVING](https://metanit.com/sql/sqlserver/5.2.php)
	Оператор HAVING определяет, какие группы будут включены в выходной результат, то есть выполняет фильтрацию групп.
Применение HAVING во многом аналогично применению WHERE. Только есть WHERE применяется к фильтрации строк, то HAVING используется для фильтрации групп.

Пример: Получить количество ПК и среднюю цену для каждой модели, средняя цена которой менее $800

    SELECT model, COUNT(model) AS Qty_model, 
       AVG(price) AS Avg_price
    FROM PC
    GROUP BY model
    HAVING AVG(price) < 800;

5.	Describe the difference between UNION and UNION ALL. 

	[UNION and UNION ALL](https://www.w3schools.com/sql/sql_union.asp) 
	The UNION operator is used to combine the result-set of two or more SELECT statements.

    * Each SELECT statement within UNION must have the same number of columns
    * The columns must also have similar data types
    * The columns in each SELECT statement must also be in the same order
```
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2; 
```
The UNION operator selects only distinct values by default. To allow duplicate values, use UNION ALL.
#Note: The column names in the result-set are usually equal to the column names in the first SELECT statement in the UNION.

6.Describe the difference between INNER and OUTER JOINs, LEFT, RIGHT.

[JOINS](https://www.w3schools.com/sql/sql_join.asp) A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

* (INNER) JOIN: Returns records that have matching values in both tables
* LEFT (OUTER) JOIN: Return all records from the left table, and the matched records from the right table
* RIGHT (OUTER) JOIN: Return all records from the right table, and the matched records from the left table
* FULL (OUTER) JOIN: Return all records when there is a match in either left or right table


7.	What is an ISOLATION LEVEL? Which of them do you know?



8.	What is ON DELETE CASCADE? What object (constraint) does it belong to?
9.	What do % and _ mean inside LIKE statement?
10.	What is deadlock? How do you simulate a deadlock for testing purpose?
11.	What is database replication? What are the different types of replication you can set up in SQL Server?

12.	Типы связей БД

	Связь работает путем сопоставления данных в ключевых столбцах; обычно это столбцы с одним и тем же именем в обеих таблицах. В большинстве случаев связь сопоставляет первичный ключ одной таблицы, являющийся уникальным идентификатором каждой строки этой таблицы, с записями внешнего ключа другой таблицы. Например продажи книг можно связать с названиями проданных книг и создать связь между столбцом title_id таблицы titles (первичный ключ) и столбцом title_id таблицы sales (внешний ключ).
	Существует три типа связей между таблицами. Тип создаваемой связи зависит от того, как определены связанные столбцы. 
	
	Связи «один ко многим» --- Связи «многие ко многим» --- Связи «один к одному»

[Habrahabr](https://habrahabr.ru/post/193380/) - Руководство по проектированию реляционных баз данных

13.	Что такое транзакция?
14.	Что такое Триггер?
15.	Что такое Функция и Хранимая процедура? Отличия

## OOP

1.	What benefits of Classes?
2.	What Incapsulation is? What benefits does it give?
3.	What Polymorphism is?
4.	What is the difference between parameters being passed to a function/method by value and by referrence?
5.	What is the difference between PosMessage and SendMessage?
6.	What is the difference between a Modal and a Modeless Dialog?
7.	What extension method is? 

Методы расширения (extension methods) позволяют добавлять новые методы в уже существующие типы без создания нового производного класса. Эта функциональность бывает особенно полезна, когда нам хочется добавить в некоторый тип новый метод, но сам тип (класс или структуру) мы изменить не можем.
Например, нам надо добавить для типа string новый метод
```
class Program {
	static void Main(string[] args){	
		string s = "Привет мир";
		char c = 'и';
		int i = s.WordCount(c);
		Console.WriteLine(i);
		Console.ReadLine();
	}
}
public static class StringExtension{
	public static int WordCount(this string str, char c){
		int counter = 0;
		for (int i = 0; i<str.Length; i++){
			if (str[i] == c)
			counter++;
		}
	return counter;
	}
} 
```

Для того, чтобы создать метод расширения, вначале надо создать статический класс, который и будет содержать этот метод. В данном случае это класс StringExtension. Затем объявляем статический метод. Суть нашего метода расширения - подсчет количества определенных символов в строке.

Собственно метод расширения - это обычный статический метод, который в качестве первого параметра всегда принимает такую конструкцию: this имя_типа название_параметра, то есть в нашем случае this string str. Так как наш метод будет относиться к типу string, то мы и используем данный тип.

Затем у всех строк мы можем вызвать данный метод: int i = s.WordCount(c);. Причем нам уже не надо указывать первый параметр. Значения для остальных параметров передаются в обычном порядке.

Применение методов расширения очень удобно, но при этом надо помнить, что метод расширения никогда не будет вызван, если он имеет ту же сигнатуру, что и метод, изначально определенный в типе.

Также следует учитывать, что методы расширения действуют на уровне пространства имен. То есть, если добавить в проект другое пространство имен, то метод не будет применяться к строкам, и в этом случае надо будет подключить пространство имен метода через директиву using.

8.	What Interface is? 
9.	What Abstract Class is? And what is the difference between Abstarct Class and Interface?
10.	What is the difference between Abstract Class and Interface

* Ссылочные типы и типы значений в C#
* Приведение типов в C#
* Boxing\Unboxing
* Generics
* Чем List отличается от Array
* Что такое сборка? Из каких частей она состоит?
* Лямбда-выражения
* Принципы работы Garbage collector

ASP.NET MVC и паттерны:
* Паттерны MVC
* Паттерны Стратегия
* Паттерны Наблюдатель
* Паттерн Фабрика
* Паттерны Repository и Unit of work

SQL:
* Выборка данных из одной таблицы по условию
* Выборка из двух таблиц с джоином
* Выборка с помощью GROUP BY
* Нормальные формы

Алгоритмические задачки:
* Найти самый большой или маленький элемент массива
* Любой алгоритм сортировки массива
* Подсчет количества вхождения подстроки в тексте

Разное:
* HTTP протокол, отличия POST запроса от GET запроса
* Что такое DOM-модель
* Отличия JavaScript от C#
* XML и JSON форматы






