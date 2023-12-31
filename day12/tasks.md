## Finally!! 🎉
You have completed the Linux & Git-GitHub handson and I hope you have learned something interesting from it.🙌

Now why not make an interesting 😉 assignment, which  not only will help you for the future but also for the DevOps Community!

Let’s make a well articulated and documented **"cheat-sheet"** with all the commands you learned so far in Linux, Git-GitHub and brief info about its usage.

Let’s  show us your knowledge mixed with your creativity😎

*I have added a [cheatsheet](https://www.sqltutorial.org/wp-content/uploads/2016/04/SQL-Cheat-Sheet-2.png) for your reference, Make sure every cheatsheet must be UNIQUE*

Post it on Linkedin and Spread the knowledge.😃 

**Happy Learning :)** 

<pre>
  yum install mariadb* -y
systemctl enable --now mariadb
systemctl status mariadb
netstat -tulpn | grep mysqld
mysql -u root -p
-p for password prompt
Enter if you have seted else hit enter

SHOW DATABASES;
exit;

mysql_secure_installaion

Set options according to you.

SHOW DATABASES;

CREATE DATABASE db_name;
</pre>



DOWNLOAD AND SETUP SSMS

https://youtu.be/iaUXjTL_F9U?si=XmwCDEGGCh-nnCmH

install SQL server 2022 Express edition

after that install ssms.

open ssms

login

CTRL + N for new query

CREATE DATABASE db_name1;

USE db_name1;

USE db_name1;
CREATE TABLE student1(
id INT PRIMARY KEY,
name VARCHAR NOT NULL,
age INT DEFAULT 0
);


DROP TABLE student1;

USE db_name1;
CREATE TABLE student(
id INT PRIMARY KEY,
name VARCHAR NOT NULL,
age INT DEFAULT 0
);

ALTER TABLE student ADD gender TEXT;

ALTER TABLE student DROP COLUMN gender;

## CONSTRAINTS :
![image](https://github.com/kmahendra999/90DaysOfDevOps/assets/9668316/6c5ce741-66c1-4f62-9d4a-65efad6fb7c5)

### Here NOT NULL IS CONSTRAINT

<pre>
CREATE TABLE Colleges (
  college_id INT NOT NULL,
  college_code VARCHAR(20) NOT NULL,
  college_name VARCHAR(50)
);
</pre>

ALTER TABLE Colleges ALTER COLUMN college_name VARCHAR(50) NOT NULL;

ALTER TABLE DROP CONSTRAINT QUERY......issue
ALTER TABLE Colleges ALTER COLUMN college_name DROP NOT NULL;

##### IN MS SQL
USE db_name1;
EXEC sp_rename 'student', 'mystudents';

#### IN my sql
USE db_name1;
ALTER TABLE student RENAME TO mystudents;

#### RENAME in SQL
USE db_name1;
EXEC sp_rename 'mystudents', 'my_students'

#### RENAME in mysql
USE db_name1;
RENAME TABLE mystudents TO my_students;

Column rename QUERY......issue

#### TRUNCATE TABLE - REMOVE ALL DATA OF TABLE
USE db_name1;
TRUNCATE TABLE my_students
