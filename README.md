# InterviewQuestionsDotNet
Junior .NET Developer tests
General
1.	What are your career goals (а) 3 years from now; (b) 10 years from now?
2.	What is SCRUM?

https://www.visualstudio.com/learn/what-is-scrum/
Scrum is a framework used by teams to manage their work. Scrum implements the principles of Agile as a concrete set of practices and roles.
 

3.	During development of a new functionality you have found a bug in existing code. What action do you take?
4.	How do you maintain your code to prove that it is a good quality code?
5.	Who/what is QA? Do we need them in the development process?
6.	What version control systems are need for? What version control systems have you worked with?
Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later.


7.	What is UAC?
8.	A custumer reports slow perormance of your application that was not reproduced in development environment. What would you suggest to do to find and localize the reason?
DB/SQL
1.	Write a query that shows all clients (FIRST NAME, LAST NAME) that occur more than once in the following client table. The query should also show how often the client occurs in the table.
Table ClientRequests

RequsetID   	INT(PK)
FirstName	Varchar(255)		
LastName 	Varchar(255)

SELECT count (RequestID) CNT, FirstName, LastName  
FROM ClientsRequests 
group by FirstName, LastName	  
having count (RequestID) > 1

2.	What is the difference between UNIQUE constraint and PRIMARY KEY constraint?
The UNIQUE constraint ensures that all values in a column are different. Both the UNIQUE and PRIMARY KEY constraints provide a guarantee for uniqueness for a column or set of columns. A PRIMARY KEY constraint automatically has a UNIQUE constraint. However, you can have many UNIQUE constraints per table, but only one PRIMARY KEY constraint per table.
	CREATE TABLE Persons (
  	  ID int NOT NULL UNIQUE,
    	LastName varchar(255) NOT NULL,
    	FirstName varchar(255),
    	Age int
	);
To name a UNIQUE constraint, and to define a UNIQUE constraint on multiple columns, use the following SQL syntax: 
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT UC_Person UNIQUE (ID,LastName)
);
The PRIMARY KEY constraint uniquely identifies each record in a database table. Primary keys must contain UNIQUE values, and cannot contain NULL values. A table can have only one primary key, which may consist of single or multiple fields.

	CREATE TABLE Persons (
    ID int NOT NULL PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
	);

3.	You have discovered a bad performing query. Describe shortly what actions you can take to optimize it.
4.	Describe the use of the HAVING clause
The HAVING clause was added to SQL because the WHERE keyword could not be used with aggregate functions.

5.	Describe the difference between UNION and UNION ALL. Describe the difference between INNER and OUTER JOINs, LEFT, RIGHT.
6.	What is an ISOLATION LEVEL? Which of them do you know?
7.	What is ON DELETE CASCADE? What object (constraint) does it belong to?
8.	What do % and _ mean inside LIKE statement?
9.	What is deadlock? How do you simulate a deadlock for testing purpose?
10.	What is database replication? What are the different types of replication you can set up in SQL Server?

11.	Типы связей БД

		Связь работает путем сопоставления данных в ключевых столбцах; обычно это столбцы с одним и тем же именем в обеих таблицах. В большинстве случаев связь сопоставляет первичный ключ одной таблицы, являющийся уникальным идентификатором каждой строки этой таблицы, с записями внешнего ключа другой таблицы. Например продажи книг можно связать с названиями проданных книг и создать связь между столбцом title_id таблицы titles (первичный ключ) и столбцом title_id таблицы sales (внешний ключ).
		Существует три типа связей между таблицами. Тип создаваемой связи зависит от того, как определены связанные столбцы. 
		Связи «один ко многим» --- Связи «многие ко многим» --- Связи «один к одному»
https://habrahabr.ru/post/193380/

12.	Что такое транзакция?
13.	Что такое Триггер?
14.	Что такое Функция и Хранимая процедура? Отличия
15.	


OOP
1.	What benefits of Classes?
2.	What Incapsulation is? What benefits does it give?
3.	What Polymorphism is?
4.	What is the difference between parameters being passed to a function/method by value and by referrence?
5.	What is the difference between PosMessage and SendMessage?
6.	What is the difference between a Modal and a Modeless Dialog?
7.	What extension method is? 
Методы расширения (extension methods) позволяют добавлять новые методы в уже существующие типы без создания нового производного класса. Эта функциональность бывает особенно полезна, когда нам хочется добавить в некоторый тип новый метод, но сам тип (класс или структуру) мы изменить не можем.
Например, нам надо добавить для типа string новый метод:
class Program
{
    static void Main(string[] args)
    {
        string s = "Привет мир";
        char c = 'и';
        int i = s.WordCount(c);
        Console.WriteLine(i);
 
        Console.ReadLine();
    }
}
 
public static class StringExtension
{
    public static int WordCount(this string str, char c)
    {
        int counter = 0;
        for (int i = 0; i<str.Length; i++)
        {
            if (str[i] == c)
                counter++;
        }
        return counter;
    }
} 

Для того, чтобы создать метод расширения, вначале надо создать статический класс, который и будет содержать этот метод. В данном случае это класс StringExtension. Затем объявляем статический метод. Суть нашего метода расширения - подсчет количества определенных символов в строке.
Собственно метод расширения - это обычный статический метод, который в качестве первого параметра всегда принимает такую конструкцию: this имя_типа название_параметра, то есть в нашем случае this string str. Так как наш метод будет относиться к типу string, то мы и используем данный тип.
Затем у всех строк мы можем вызвать данный метод: int i = s.WordCount(c);. Причем нам уже не надо указывать первый параметр. Значения для остальных параметров передаются в обычном порядке.
Применение методов расширения очень удобно, но при этом надо помнить, что метод расширения никогда не будет вызван, если он имеет ту же сигнатуру, что и метод, изначально определенный в типе.
Также следует учитывать, что методы расширения действуют на уровне пространства имен. То есть, если добавить в проект другое пространство имен, то метод не будет применяться к строкам, и в этом случае надо будет подключить пространство имен метода через директиву using.
8.	What Interface is? 
9.	What Abstrct Class is? And what is the difference between Abstarct Class and Interface?
10.	What is the difference between Abstarct Class and Interface






