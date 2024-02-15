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
  
*************
  
<pre>
  [root@control ~]# mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MariaDB
root user without the proper authorisation.

Set root password? [Y/n] y 
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] Y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] Y
 ... Success!

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] Y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] Y
 ... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!
[root@control ~]# 


  You can Set options according to you.
</pre>
*************


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
*******************************
## QUERIES

CREATE DATABASE db_name1;
DROP DATABASE db_name1;

CREATE DATABASE db_name1;

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


### PRACTICE IN MYSQL/MARIADB :
CREATE TABLE table_name(id INT PRIMARY KEY, name VARCHAR(255) NOT NULL, price INT DEFAULT 0);

DROP TABLE table_name;

CREATE TABLE table_name(id INT PRIMARY KEY, name VARCHAR(255) NOT NULL, price INT DEFAULT 0);

ALTER TABLE table_name ADD column c INT;

ALTER TABLE table_name DROP COLUMN c;

ALTER TABLE table_name MODIFY COLUMN c INT NOT NULL;

ALTER TABLE table_name RENAME TO table_name1;

ALTER TABLE table_name CHANGE COLUMN id sid INT;

TRUNCATE TABLE table_name;

+===========================================

## USING SQL CONSTRAINT

CREATE TABLE t(c1 INT, c2 INT, c3 VARCHAR(255), PRIMARY KEY(c1,c2));

CREATE TABLE t2(c2 INT PRIMARY KEY);

CREATE TABLE t1(c1 INT PRIMARY KEY, c2 INT, FOREIGN KEY(c2) REFERENCES t2(c2));

CREATE TABLE t(c1 INT, c2 INT, C3 INT, UNIQUE(c2,c3));

CREATE TABLE t(c1 INT, c2 INT, CHECK(c1>0 AND c1>=C2));

CREATE TABLE t11(c1 INT PRIMARY KEY, c2 VARCHAR(255) NOT NULL);

+============================================

### MODIFYING DATA

SHOW COLUMNS FROM table_name;

INSERT INTO table_name(id, name, price) VALUES(001, 'Mahendra Kumar', 23);

INSERT INTO table_name(id, name, price) VALUES(002, 'Raghvendra', 25), (003, 'Jitendra', 36), (004,"SING JI",45);

#CREATE TABLE table_new(id INT PRIMARY KEY, name VARCHAR(255) NOT NULL, price INT DEFAULT 0);

INSERT INTO table_new SELECT * FROM table_name;

SELECT * FROM table_new;

UPDATE table_new SET price = 25;

UPDATE table_new SET name="Mahendra Kumar", price=85;

INSERT INTO table_name(id, name, price) VALUES(005, 'Raghvendra', 65), (006, 'Jitendra', 36), (007,"SING JI",45);

<pre>
SELECT * FROM table_name;
+----+----------------+-------+
| id | name           | price |
+----+----------------+-------+
|  1 | Mahendra Kumar |    23 |
|  2 | Raghvendra     |    25 |
|  3 | Jitendra       |    36 |
|  4 | SING JI        |    45 |
|  5 | Raghvendra     |    65 |
|  6 | Jitendra       |    36 |
|  7 | SING JI        |    45 |
+----+----------------+-------+

MariaDB [grras]> DELETE FROM table_name WHERE price=45;
Query OK, 2 rows affected (0.001 sec)

MariaDB [grras]> SELECT * FROM table_name;
+----+----------------+-------+
| id | name           | price |
+----+----------------+-------+
|  1 | Mahendra Kumar |    23 |
|  2 | Raghvendra     |    25 |
|  3 | Jitendra       |    36 |
|  5 | Raghvendra     |    65 |
|  6 | Jitendra       |    36 |
+----+----------------+-------+
5 rows in set (0.000 sec)

MariaDB [grras]> DELETE FROM table_name;
Query OK, 5 rows affected (0.001 sec)

MariaDB [grras]> SELECT * FROM table_name;
Empty set (0.000 sec)

MariaDB [grras]> 

</pre>

These are testing querires for your practice.
<pre>
  ----> log into database ( in case of error make sure your database is running at localhost on port number 3306)

#mysql -u root -p 

----> full command  mysql --host hostname --port 3306 --user username --database dbname -p 

---> for creating a database 

#CREATE DATABASE student CHARACTER SET utf8;

----> select created database student

#USE student;

----> create a table called student

#CREATE TABLE student(sid INT(5) NOT NULL auto_increment, name VARCHAR(50) NOT NULL, ph_no VARCHAR(13) DEFAULT 'NA',email VARCHAR(50) NOT NULL, CONSTRAINT pk PRIMARY KEY  (sid) );

----> create a table called address connected to student

#CREATE TABLE address(addr_id INT(3) NOT NULL PRIMARY KEY AUTO_INCREMENT,sid INT(5) NOT NULL, house_no VARCHAR(10),street VARCHAR(100), area VARCHAR(200), land_marks VARCHAR(200), city VARCHAR(50) NOT NULL, state VARCHAR(50) NOT NULL, country VARCHAR(50) NOT NULL,pincode INT(6) NOT NULL, CONSTRAINT fk_student FOREIGN KEY (sid) REFERENCES student(sid) ON DELETE CASCADE ON UPDATE NO ACTION );

----> create a table called fees 

#CREATE TABLE fees(fid INT(5) NOT NULL PRIMARY KEY AUTO_INCREMENT, sid INT(3) NOT NULL, due DOUBLE, fees DOUBLE, discount DOUBLE,CONSTRAINT student_fk FOREIGN KEY (sid) REFERENCES student(sid) );

----> create a table called course

# CREATE TABLE course(cid INT(5) NOT NULL PRIMARY KEY,sid INT(5) NOT NULL,name VARCHAR(100), CONSTRAINT fk_course FOREIGN KEY (sid) REFERENCES student(sid) );


----> show tables in student databases

#SHOW TABLES;

----> let's see schema of student table

#DESCRIBE student;

----> let's see schema of address table

#DESCRIBE address;

----> let's see schema of fees table 

#DESCRIBE fees;

#DESCRIBE course;

-----> now create a admin user for student database 

----> to delete users from database 

#DELETE FROM mysql.user WHERE user='student';
----> DELETE FROM database.tablename WHERE user='username'

#CREATE USER 'student'@'localhost' IDENTIFIED BY 'student';

----> for remote user give usernameas --> 'student'@'domain.com' or 'student'@'192.168.5.10' or 'student'@'%'


----> now grant permission to newley created user on all tables of student database

#GRANT ALL PRIVILEGES ON student.* TO 'student'@'localhost';

----> if want to remove privileges just REVOKE instead of grant
----> create a user who can only fire select command to student database 

#CREATE USER 'st'@'localhost' IDENTIFIED BY 'student';

----> grant only select query on student database tables 

#GRANT SELECT ON student.* TO 'st'@'localhost'; 

----> use SELECT,UPDATE,INSERT,... to provide more privileges to an user or for specific table use student.table name as student.address or so 

----> to verify privileges just logout by command exit and login with user privileges

#EXIT;

#mysql -u student -p student

----> lets check select privileges 

#SELECT * FROM student;

----> it will work now create a table 

#CREATE TABLE new_table (id TEXT,data BLOB);

----> BLOB is data type of mariadb and you will see table will be created

----> Now let's delete the table 

#DROP TABLE new_table;


----> logout again 

#EXIT 


----> login with different user 

#mysql -u st -p student

----> show table command 

#SHOW TABLES;

----> fire select query on student table

#SELECT * FROM student;

----> now try to create table 

#CREATE TABLE new_table(id int(5));

----> you will get error message as st user does not have permission of maniplutation 

#EXIT


#mysql -u student -p student
</pre>
