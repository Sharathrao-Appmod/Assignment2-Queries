Step 1 : Linux new-instance-sharath 5.10.0-27-cloud-amd64 #1 SMP Debian 5.10.205-2 (2023-12-31) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Thu Jan 11 04:51:08 2024 from 35.235.241.129
sharath_rao_niveussolutions_com@new-instance-sharath:~$ psql -h 172.16.60.3 -d sample-sharth -U postgres
Password for user postgres: 
psql (13.13 (Debian 13.13-0+deb11u1), server 15.4)
WARNING: psql major version 13, server major version 15.
         Some psql features might not work.
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

Step 2 : sample-sharth=> \l
                                                  List of databases
       Name       |       Owner       | Encoding |  Collate   |   Ctype    |            Access privileges            
------------------+-------------------+----------+------------+------------+-----------------------------------------
 cloudsqladmin    | cloudsqladmin     | UTF8     | en_US.UTF8 | en_US.UTF8 | 
 employee         | cloudsqlsuperuser | UTF8     | en_US.UTF8 | en_US.UTF8 | 
 postgres         | cloudsqlsuperuser | UTF8     | en_US.UTF8 | en_US.UTF8 | 
 sample-sharth    | cloudsqlsuperuser | UTF8     | en_US.UTF8 | en_US.UTF8 | 
 student_database | cloudsqlsuperuser | UTF8     | en_US.UTF8 | en_US.UTF8 | 
 template0        | cloudsqladmin     | UTF8     | en_US.UTF8 | en_US.UTF8 | =c/cloudsqladmin                       +
                  |                   |          |            |            | cloudsqladmin=CTc/cloudsqladmin
 template1        | cloudsqlsuperuser | UTF8     | en_US.UTF8 | en_US.UTF8 | =c/cloudsqlsuperuser                   +
                  |                   |          |            |            | cloudsqlsuperuser=CTc/cloudsqlsuperuser
(7 rows)

Step 3 : sample-sharth=> CREATE USER sharath WITH PASSWORD 'niveus@123';
CREATE ROLE
Step 4 : sample-sharth=> CREATE DATABASE employee1;
CREATE DATABASE
Step 4 : sample-sharth=> ALTER ROLE sharath SET client_encoding TO 'utf8';
ALTER ROLE
Step 5 : sample-sharth=> ALTER ROLE sharath SET default_transaction_isolation TO 'read committed';
ALTER ROLE
Step 6 : sample-sharth=> ALTER ROLE sharath SET timezone TO 'UTC';
ALTER ROLE
Step 7 : sample-sharth=> GRANT ALL PRIVILEGES ON DATABASE employee1 TO sharath;
GRANT
Step 8 : sample-sharth=> GRANT ALL ON SCHEMA public TO sharath;
GRANT
Step 9 : sample-sharth=> GRANT ALL PRIVILEGES ON TABLE COMPANY TO sharath;
GRANT
sample-sharth=> \l
                                                  List of databases
       Name       |       Owner       | Encoding |  Collate   |   Ctype    |            Access privileges            
------------------+-------------------+----------+------------+------------+-----------------------------------------
 cloudsqladmin    | cloudsqladmin     | UTF8     | en_US.UTF8 | en_US.UTF8 | 
 employee         | cloudsqlsuperuser | UTF8     | en_US.UTF8 | en_US.UTF8 | 
 employee1        | postgres          | UTF8     | en_US.UTF8 | en_US.UTF8 | =Tc/postgres                           +
                  |                   |          |            |            | postgres=CTc/postgres                  +
                  |                   |          |            |            | sharath=CTc/postgres
 postgres         | cloudsqlsuperuser | UTF8     | en_US.UTF8 | en_US.UTF8 | 
 sample-sharth    | cloudsqlsuperuser | UTF8     | en_US.UTF8 | en_US.UTF8 | 
 student_database | cloudsqlsuperuser | UTF8     | en_US.UTF8 | en_US.UTF8 | 
 template0        | cloudsqladmin     | UTF8     | en_US.UTF8 | en_US.UTF8 | =c/cloudsqladmin                       +
                  |                   |          |            |            | cloudsqladmin=CTc/cloudsqladmin
 template1        | cloudsqlsuperuser | UTF8     | en_US.UTF8 | en_US.UTF8 | =c/cloudsqlsuperuser                   +
                  |                   |          |            |            | cloudsqlsuperuser=CTc/cloudsqlsuperuser
(8 rows)

Step 10 : sample-sharth=> \c employee1
psql (13.13 (Debian 13.13-0+deb11u1), server 15.4)
WARNING: psql major version 13, server major version 15.
         Some psql features might not work.
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
You are now connected to database "employee1" as user "postgres".
Step 11 : employee1=> CREATE TABLE COMPANY(
                    ID INT PRIMARY KEY     NOT NULL,
                    NAME           TEXT    NOT NULL,
                    AGE            INT     NOT NULL,
                    ADDRESS        CHAR(50),
                    SALARY         REAL
                    );
CREATE TABLE
Step 12 : employee1=> CREATE TABLE DEPARTMENT(
                    ID INT PRIMARY KEY      NOT NULL,
                    DEPT           CHAR(50) NOT NULL,
                    EMP_ID         INT      NOT NULL
                    );
CREATE TABLE
Step 13 : INSERT to the table
employee1=> INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) VALUES (1, 'Harish', 32, 'Udupi', 20000.00);
INSERT 0 1
employee1=> INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) VALUES (2, 'Umesh', 25, 'Kundapura', 30000.00);
INSERT 0 1
employee1=> INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) VALUES (3, 'Sathish', 23, 'Santhekatte', 20000.00);
INSERT 0 1
employee1=> INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) VALUES (4, 'Suresh', 25, 'Mangaluru ', 65000.00);
INSERT 0 1
employee1=> INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) VALUES (5, 'Ramesh', 27, 'Puttur', 85000.00);
INSERT 0 1
employee1=> SELECT * FROM COMPANY;
 id |  name   | age |                      address                       | salary 
----+---------+-----+----------------------------------------------------+--------
  1 | Harish  |  32 | Udupi                                              |  20000
  2 | Umesh   |  25 | Kundapura                                          |  30000
  3 | Sathish |  23 | Santhekatte                                        |  20000
  4 | Suresh  |  25 | Mangaluru                                          |  65000
  5 | Ramesh  |  27 | Puttur                                             |  85000
(5 rows)

employee1=> INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) VALUES (12, 'Rajesh', 26, 'Udupi', 20000.00);
INSERT 0 1
employee1=> INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) VALUES (11, 'Raj', 28, 'Kodibengre', 30000.00);
INSERT 0 1
Step 14 : employee1=> SELECT * FROM COMPANY;
 id |  name   | age |                      address                       | salary 
----+---------+-----+----------------------------------------------------+--------
  1 | Harish  |  32 | Udupi                                              |  20000
  2 | Umesh   |  25 | Kundapura                                          |  30000
  3 | Sathish |  23 | Santhekatte                                        |  20000
  4 | Suresh  |  25 | Mangaluru                                          |  65000
  5 | Ramesh  |  27 | Puttur                                             |  85000
 12 | Rajesh  |  26 | Udupi                                              |  20000
 11 | Raj     |  28 | Kodibengre                                         |  30000
(7 rows)

Step 15 : SELECT from the table
employee1=> SELECT ID, NAME, SALARY FROM COMPANY;
 id |  name   | salary 
----+---------+--------
  1 | Harish  |  20000
  2 | Umesh   |  30000
  3 | Sathish |  20000
  4 | Suresh  |  65000
  5 | Ramesh  |  85000
 12 | Rajesh  |  20000
 11 | Raj     |  30000
(7 rows)

Step 16 : UPDATE the table
employee1=> UPDATE COMPANY SET SALARY = 15000 WHERE ID = 3;
UPDATE 1
employee1=> SELECT * FROM COMPANY;
 id |  name   | age |                      address                       | salary 
----+---------+-----+----------------------------------------------------+--------
  1 | Harish  |  32 | Udupi                                              |  20000
  2 | Umesh   |  25 | Kundapura                                          |  30000
  4 | Suresh  |  25 | Mangaluru                                          |  65000
  5 | Ramesh  |  27 | Puttur                                             |  85000
 12 | Rajesh  |  26 | Udupi                                              |  20000
 11 | Raj     |  28 | Kodibengre                                         |  30000
  3 | Sathish |  23 | Santhekatte                                        |  15000
(7 rows)

Step 17 : DELETE from the table
employee1=> DELETE FROM COMPANY WHERE ID = 2;
DELETE 1
employee1=> SELECT * FROM COMPANY;
 id |  name   | age |                      address                       | salary 
----+---------+-----+----------------------------------------------------+--------
  1 | Harish  |  32 | Udupi                                              |  20000
  4 | Suresh  |  25 | Mangaluru                                          |  65000
  5 | Ramesh  |  27 | Puttur                                             |  85000
 12 | Rajesh  |  26 | Udupi                                              |  20000
 11 | Raj     |  28 | Kodibengre                                         |  30000
  3 | Sathish |  23 | Santhekatte                                        |  15000
(6 rows)
