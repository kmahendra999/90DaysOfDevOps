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
firewall-cmd --permanent --add-port=3306/tcp
firewall-cmd --reload
****
SSH KE CASE ME PORT DEFAULT PUBLICH HOTA HE CHECK KE LIYE : firewall-cmd --get-defaults-zone
abhi firewall me kya allowed he check ke liye
vim /etc/firewalld/zones/public.xml
****
mysql -u root -p
-p for password prompt
Enter if you have seted else hit enter

SHOW DATABASES;
exit;

mysql_secure_installaion

Set options according to you.

SHOW DATABASES;

CREATE DATABASE db_name;
use db_name;
SHOW TABLES;
DESCRIBE TABLE_NAME;

SELECT * FROM TABLE_NAME WHERE column=value;

************
user creation in databse servers.

mysql -u root -p
CREATE USER gaurav@'localhost' identified by 'redhat';
localhost can be % also for all host allowd for login.

SELECT User, Host from user;

***************
Giving permission to users for see tables.

mysql -u root -p
grant all on TABLE_NAME.* to gaurav@localhost;
all = all permisiion 
* = all columns

**************
removing user permission
revoke all on mysql.user from gaurav@localhost;

*************
Removing user

DROP USER 'gaurav'@localhost


******************
BACK UP
mysqldump -u root -p DB_NAME > /tmp/abc.dump

cat / vim /tmp/abc.dump


mysqldump -u root -p --all-databases > /tmp/abdc.dump
******************
RESTORE
mysql -u root -p DB_name1 < /tmp/abc.dump

search on google
mariadb configuraion options
vim /etc/my.cnf.d/mariadb-server.cnf
vim /etc/my.cnf.d/mariadb-client.cnf
systemctl restart mariadb

databsae ka data directory
/var/lib/mysql/

logs ka direcoty
ls -l /var/log/mariadb/mariadb.log


DB SERVER KA PHYSICAL BACKUP
db server /var/lib/mysql ko kisi dive pe mount karwa kar like /datadrive and us drive ka lvm snapshot liya.
and ab hum us snapshot se mysqldump command se bankup lenge to db server par load nahi rahega.

DB SERVER KA LOGICAL BACKUP my sql dump command se lena.

HOT BACKUP --- MACHINE CHAL RAHI HE AND RUN TIME PAR BACKUP LIYA
COLD BACKUP --- SERVER KO BAND KARKE BACKUP LENA





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
