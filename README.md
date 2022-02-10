# MySQL Queries Practice

### Basic Queries

show databases;<br>
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| test               |
+--------------------+<br>
5 rows in set (0.00 sec)<br>

mysql> create database document;   --DDL Command
Query OK, 1 row affected (0.01 sec)

mysql> use document;
Database changed
mysql> show tables;
Empty set (0.00 sec)

mysql> create table friends(id tinyint primary key,name varchar(30) not null,favourite_color varchar(20) default "Black");        --DDL Command
Query OK, 0 rows affected (0.05 sec)

mysql> desc friends;
+-----------------+-------------+------+-----+---------+-------+
| Field           | Type        | Null | Key | Default | Extra |
+-----------------+-------------+------+-----+---------+-------+
| id              | tinyint     | NO   | PRI | NULL    |       |
| name            | varchar(30) | NO   |     | NULL    |       |
| favourite_color | varchar(20) | YES  |     | Black   |       |
+-----------------+-------------+------+-----+---------+-------+
3 rows in set (0.01 sec)

mysql> show tables;
+--------------------+
| Tables_in_document |
+--------------------+
| friends            |
+--------------------+
1 row in set (0.00 sec)

mysql> insert into friends values(1,"Ismail","Purple");      --DML Command
Query OK, 1 row affected (0.03 sec)

mysql> insert into friends values(2,"Rishi","Green");
Query OK, 1 row affected (0.01 sec)

mysql> insert into friends values(3,"Vaishnavi","Blue");
Query OK, 1 row affected (0.00 sec)

mysql> insert into friends(id,name) values(4,"Meenu");
Query OK, 1 row affected (0.01 sec)

mysql> select * from friends;     --DML Command
+----+-----------+-----------------+
| id | name      | favourite_color |
+----+-----------+-----------------+
|  1 | Ismail    | Purple          |
|  2 | Rishi     | Green           |
|  3 | Vaishnavi | Blue            |
|  4 | Meenu     | Black           |
+----+-----------+-----------------+
4 rows in set (0.00 sec)

mysql> update friends set name="Girls"  --DML Command
    -> where id between 1 and 3;
Query OK, 3 rows affected (0.01 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> select * from friends;
+----+-------+-----------------+
| id | name  | favourite_color |
+----+-------+-----------------+
|  1 | Girls | Purple          |
|  2 | Girls | Green           |
|  3 | Girls | Blue            |
|  4 | Meenu | Black           |
+----+-------+-----------------+
4 rows in set (0.00 sec)

mysql> alter table friends add (marks tinyint check (marks>30));   --DDL Command
Query OK, 4 rows affected (0.10 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> desc friends;
+-----------------+-------------+------+-----+---------+-------+
| Field           | Type        | Null | Key | Default | Extra |
+-----------------+-------------+------+-----+---------+-------+
| id              | tinyint     | NO   | PRI | NULL    |       |
| name            | varchar(30) | NO   |     | NULL    |       |
| favourite_color | varchar(20) | YES  |     | Black   |       |
| marks           | tinyint     | YES  |     | NULL    |       |
+-----------------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> alter table friends change favourite_color favColor varchar(30);
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc friends;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| id       | tinyint     | NO   | PRI | NULL    |       |
| name     | varchar(30) | NO   |     | NULL    |       |
| favColor | varchar(30) | YES  |     | NULL    |       |
| marks    | tinyint     | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> alter table friends modify favColor varchar(12);
Query OK, 4 rows affected (0.11 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> desc friends;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| id       | tinyint     | NO   | PRI | NULL    |       |
| name     | varchar(30) | NO   |     | NULL    |       |
| favColor | varchar(12) | YES  |     | NULL    |       |
| marks    | tinyint     | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> select * from friends;
+----+-------+----------+-------+
| id | name  | favColor | marks |
+----+-------+----------+-------+
|  1 | Girls | Purple   |  NULL |
|  2 | Girls | Green    |  NULL |
|  3 | Girls | Blue     |  NULL |
|  4 | Meenu | Black    |  NULL |
+----+-------+----------+-------+
4 rows in set (0.00 sec)

mysql> update friends set marks=100;
Query OK, 4 rows affected (0.00 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> select * from friends;
+----+-------+----------+-------+
| id | name  | favColor | marks |
+----+-------+----------+-------+
|  1 | Girls | Purple   |   100 |
|  2 | Girls | Green    |   100 |
|  3 | Girls | Blue     |   100 |
|  4 | Meenu | Black    |   100 |
+----+-------+----------+-------+
4 rows in set (0.00 sec)

mysql> use test;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+----------------+
| Tables_in_test |
+----------------+
| Meenu          |
| Pr             |
| Sowjanya       |
| students       |
+----------------+
4 rows in set (0.01 sec)

mysql> drop table Pr;     --DDL Command
Query OK, 0 rows affected (0.03 sec)

mysql> show tables;
+----------------+
| Tables_in_test |
+----------------+
| Meenu          |
| Sowjanya       |
| students       |
+----------------+
3 rows in set (0.00 sec)

mysql> select * from students;
+----+-------------------------+-------+-------+-------+
| id | name                    | class | mark1 | mark2 |
+----+-------------------------+-------+-------+-------+
|  1 | Arun Kumar              | X     |    12 |    24 |
|  2 | Aro Jobin               | X     |    10 |    10 |
|  3 | Arockiya Joshua         | X     |    10 |     5 |
|  4 | Antony Kaplisom         | X     |    10 |    23 |
|  5 | Keerthana               | X     |     0 |     0 |
|  6 | Kaushik                 | X     |    12 |     2 |
|  7 | Dhanush                 | X     |    12 |     2 |
|  8 | Freddy                  | X     |    12 |     2 |
|  9 | Gopi                    | X     |    72 |     5 |
| 10 | Mukesh                  | X     |     2 |     5 |
| 11 | Mounicka                | X     |     0 |     0 |
| 12 | Meenu Sowjanya          | X     |   100 |   100 |
| 13 | Pradeep Selva Kumar     | X     |   100 |   100 |
| 14 | Lincy Niranjana         | X     |    10 |    10 |
| 15 | Prescilla               | X     |    10 |    10 |
| 16 | Linu Uprasi             | X     |    10 |    10 |
| 17 | Nivethita               | X     |    10 |    10 |
| 18 | Sneha                   | X     |    10 |    10 |
| 19 | Revathi                 | X     |   100 |   100 |
| 20 | Indhira Priya Dharshini | X     |     0 |     0 |
| 21 | Rithika                 | X     |     0 |     0 |
| 22 | Meena                   | X     |     0 |     0 |
| 23 | Mohammed Raffiee        | X     |     0 |     0 |
| 24 | Mohammed Riffayudeen    | X     |     0 |     0 |
| 25 | Kamalesh                | X     |     0 |     0 |
| 26 | Rajapalani              | X     |     0 |     0 |
| 27 | Vibeena                 | X     |     0 |     0 |
| 28 | Rohan Britto            | X     |   100 |   100 |
| 29 | Abishek Ilambirithi     | X     |   100 |   100 |
| 30 | Shrinithi               | X     |    30 |    75 |
| 31 | Hemashree               | X     |    20 |    15 |
| 32 | Shajitha                | X     |    -2 |    -5 |
| 33 | Rohith Kumar            | X     |    75 |    40 |
| 34 | Shyamala                | X     |    40 |    40 |
| 35 | Jerry Winston           | X     |    40 |    40 |
| 36 | Sam Wilson              | X     |    30 |    10 |
| 37 | Vishwa                  | X     |   100 |   100 |
| 38 | Isai Visahan            | X     |    10 |     5 |
| 39 | Pooja                   | X     |     0 |     0 |
| 40 | Deva Dharshini          | X     |   -10 |   -10 |
| 41 | DevaDharshini           | X     |   -10 |   -10 |
| 42 | Abdul Majeeth           | X     |   100 |   100 |
| 43 | Subashan                | X     |     0 |     0 |
| 44 | Hemachandran            | X     |   100 |   100 |
| 45 | Dhinesh                 | X     |    10 |    10 |
| 46 | Swarna                  | X     |     0 |     0 |
| 47 | Swathika                | X     |     0 |     0 |
| 48 | Adithya                 | X     |     0 |     0 |
| 49 | Richard                 | X     |     0 |     0 |
| 50 | Saran Kumar             | X     |     0 |     0 |
+----+-------------------------+-------+-------+-------+
50 rows in set (0.00 sec)

mysql> delete from students where id between 14 and 50;
Query OK, 37 rows affected (0.01 sec)

mysql> select * from students;
+----+---------------------+-------+-------+-------+
| id | name                | class | mark1 | mark2 |
+----+---------------------+-------+-------+-------+
|  1 | Arun Kumar          | X     |    12 |    24 |
|  2 | Aro Jobin           | X     |    10 |    10 |
|  3 | Arockiya Joshua     | X     |    10 |     5 |
|  4 | Antony Kaplisom     | X     |    10 |    23 |
|  5 | Keerthana           | X     |     0 |     0 |
|  6 | Kaushik             | X     |    12 |     2 |
|  7 | Dhanush             | X     |    12 |     2 |
|  8 | Freddy              | X     |    12 |     2 |
|  9 | Gopi                | X     |    72 |     5 |
| 10 | Mukesh              | X     |     2 |     5 |
| 11 | Mounicka            | X     |     0 |     0 |
| 12 | Meenu Sowjanya      | X     |   100 |   100 |
| 13 | Pradeep Selva Kumar | X     |   100 |   100 |
+----+---------------------+-------+-------+-------+
13 rows in set (0.00 sec)

mysql> desc students;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   | PRI | NULL    |       |
| name  | varchar(30) | NO   |     | NULL    |       |
| class | varchar(2)  | NO   |     | NULL    |       |
| mark1 | int         | YES  |     | 0       |       |
| mark2 | int         | YES  |     | 0       |       |
+-------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> alter table students drop column mark2;
Query OK, 0 rows affected (0.08 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc students;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | NO   | PRI | NULL    |       |
| name  | varchar(30) | NO   |     | NULL    |       |
| class | varchar(2)  | NO   |     | NULL    |       |
| mark1 | int         | YES  |     | 0       |       |
+-------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> use document;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed

mysql> select * from friends;
+----+-------+----------+-------+
| id | name  | favColor | marks |
+----+-------+----------+-------+
|  1 | Girls | Purple   |   100 |
|  2 | Girls | Green    |   100 |
|  3 | Girls | Blue     |   100 |
|  4 | Meenu | Black    |   100 |
+----+-------+----------+-------+
4 rows in set (0.01 sec)

mysql> select 4*3 as answer,name as friends from friends where favColor like("B%");
+--------+---------+
| answer | friends |
+--------+---------+
|     12 | Girls   |
|     12 | Meenu   |
+--------+---------+
2 rows in set (0.01 sec)

mysql> insert into friends(id,name) values(5,"Rishi");
Query OK, 1 row affected (0.00 sec)

mysql> select * from friends;
+----+-------+----------+-------+
| id | name  | favColor | marks |
+----+-------+----------+-------+
|  1 | Girls | Purple   |   100 |
|  2 | Girls | Green    |   100 |
|  3 | Girls | Blue     |   100 |
|  4 | Meenu | Black    |   100 |
|  5 | Rishi | NULL     |  NULL |
+----+-------+----------+-------+
5 rows in set (0.00 sec)

mysql> select id,name,ifnull(favColor,"Nothing to specify"),ifnull(marks,"Absent") from friends;
+----+-------+---------------------------------------+------------------------+
| id | name  | ifnull(favColor,"Nothing to specify") | ifnull(marks,"Absent") |
+----+-------+---------------------------------------+------------------------+
|  1 | Girls | Purple                                | 100                    |
|  2 | Girls | Green                                 | 100                    |
|  3 | Girls | Blue                                  | 100                    |
|  4 | Meenu | Black                                 | 100                    |
|  5 | Rishi | Nothing to specify                    | Absent                 |
+----+-------+---------------------------------------+------------------------+
5 rows in set (0.00 sec)

mysql> select ifnull(favColor,"Nothing to specify") from friends order by favColor;
+---------------------------------------+
| ifnull(favColor,"Nothing to specify") |
+---------------------------------------+
| Nothing to specify                    |
| Black                                 |
| Blue                                  |
| Green                                 |
| Purple                                |
+---------------------------------------+
5 rows in set (0.00 sec)

mysql> select ifnull(favColor,"Nothing to specify") from friends order by favColor desc;
+---------------------------------------+
| ifnull(favColor,"Nothing to specify") |
+---------------------------------------+
| Purple                                |
| Green                                 |
| Blue                                  |
| Black                                 |
| Nothing to specify                    |
+---------------------------------------+
5 rows in set (0.01 sec)

mysql> /* Mysql Functions */
mysql> select char(70,65,67,69);
+--------------------------------------+
| char(70,65,67,69)                    |
+--------------------------------------+
| 0x46414345                           |
+--------------------------------------+
1 row in set (0.00 sec)

mysql> select concat(name,id) from friends;
+-----------------+
| concat(name,id) |
+-----------------+
| Girls1          |
| Girls2          |
| Girls3          |
| Meenu4          |
| Rishi5          |
+-----------------+
5 rows in set (0.00 sec)

mysql> select lower("Meenu Sowjanya") as lower,lcase("Meenu Sowjanya") as lcase,upper("Meenu Sowjanya") as upper,ucase("Meenu Sowjanya") as ucase;
+----------------+----------------+----------------+----------------+
| lower          | lcase          | upper          | ucase          |
+----------------+----------------+----------------+----------------+
| meenu sowjanya | meenu sowjanya | MEENU SOWJANYA | MEENU SOWJANYA |
+----------------+----------------+----------------+----------------+
1 row in set (0.00 sec)

mysql> select substring("Meenu Sowjanya",-5,4) as substring,substr("Meenu Sowjanya",3,4) as substr;
+-----------+--------+
| substring | substr |
+-----------+--------+
| jany      | enu    |
+-----------+--------+
1 row in set (0.00 sec)

mysql> select trim("     Meenu   Sowjanya            ") as trim;
+------------------+
| trim             |
+------------------+
| Meenu   Sowjanya |
+------------------+
1 row in set (0.00 sec)

mysql> select length("Meenu Sowjanya") as length;
+--------+
| length |
+--------+
|     14 |
+--------+
1 row in set (0.00 sec)

mysql> select mod(11,4) as modulus,power(3,2) as power,pow(9,2) as power1,round(15.1293874,2) as rounded_to_2_decimals,sign(12) as sign_of_no,sqrt(26) as square_root,truncate(15.827283928,1) as truncate1,truncate(157.374683,0) as truncate2;
+---------+-------+--------+-----------------------+------------+--------------------+-----------+-----------+
| modulus | power | power1 | rounded_to_2_decimals | sign_of_no | square_root        | truncate1 | truncate2 |
+---------+-------+--------+-----------------------+------------+--------------------+-----------+-----------+
|       3 |     9 |     81 |                 15.13 |          1 | 5.0990195135927845 |      15.8 |       157 |
+---------+-------+--------+-----------------------+------------+--------------------+-----------+-----------+
1 row in set (0.00 sec)

mysql> select curdate(),current_date(),current_date,date("2003-09-24 01:02:03"),month("2003-09-24"),year("2003-09-24"),now();
+------------+----------------+--------------+-----------------------------+---------------------+--------------------+---------------------+
| curdate()  | current_date() | current_date | date("2003-09-24 01:02:03") | month("2003-09-24") | year("2003-09-24") | now()               |
+------------+----------------+--------------+-----------------------------+---------------------+--------------------+---------------------+
| 2022-02-04 | 2022-02-04     | 2022-02-04   | 2003-09-24                  |                   9 |               2003 | 2022-02-04 21:28:16 |
+------------+----------------+--------------+-----------------------------+---------------------+--------------------+---------------------+
1 row in set (0.00 sec)

mysql> /* Aggregate functions */
mysql> use test;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> select * from students;
+----+---------------------+-------+-------+
| id | name                | class | mark1 |
+----+---------------------+-------+-------+
|  1 | Arun Kumar          | X     |    12 |
|  2 | Aro Jobin           | X     |    10 |
|  3 | Arockiya Joshua     | X     |    10 |
|  4 | Antony Kaplisom     | X     |    10 |
|  5 | Keerthana           | X     |     0 |
|  6 | Kaushik             | X     |    12 |
|  7 | Dhanush             | X     |    12 |
|  8 | Freddy              | X     |    12 |
|  9 | Gopi                | X     |    72 |
| 10 | Mukesh              | X     |     2 |
| 11 | Mounicka            | X     |     0 |
| 12 | Meenu Sowjanya      | X     |   100 |
| 13 | Pradeep Selva Kumar | X     |   100 |
+----+---------------------+-------+-------+
13 rows in set (0.00 sec)


mysql> select distinct(mark1),count(*),count(distinct(mark1)),max(mark1),min(mark1),sum(distinct(mark1)) from students group by mark1;
+-------+----------+------------------------+------------+------------+----------------------+
| mark1 | count(*) | count(distinct(mark1)) | max(mark1) | min(mark1) | sum(distinct(mark1)) |
+-------+----------+------------------------+------------+------------+----------------------+
|     0 |        2 |                      1 |          0 |          0 |                    0 |
|     2 |        1 |                      1 |          2 |          2 |                    2 |
|    10 |        3 |                      1 |         10 |         10 |                   10 |
|    12 |        4 |                      1 |         12 |         12 |                   12 |
|    72 |        1 |                      1 |         72 |         72 |                   72 |
|   100 |        2 |                      1 |        100 |        100 |                  100 |
+-------+----------+------------------------+------------+------------+----------------------+
6 rows in set (0.00 sec)

### MySQL Constraints Practice



mysql> use test;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> create table uSquare(id tinyint primary key,name varchar(30) not null,roll tinyint unique not null,age tinyint check(age>=1) not null);
Query OK, 0 rows affected (0.07 sec)

mysql> desc uSquare;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | tinyint     | NO   | PRI | NULL    |       |
| name  | varchar(30) | NO   |     | NULL    |       |
| roll  | tinyint     | NO   | UNI | NULL    |       |
| age   | tinyint     | NO   |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> create table United(foreign key(id) references uSquare(id),name varchar(30) not null,mark tinyint default "Absent");

mysql> create table United(roll tinyint primary key,name varchar(20) not null,id tinyint,marks tinyint default 0,foreign key(id) references uSquare(id));
Query OK, 0 rows affected (0.04 sec)

mysql> desc United;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| roll  | tinyint     | NO   | PRI | NULL    |       |
| name  | varchar(20) | NO   |     | NULL    |       |
| id    | tinyint     | YES  | MUL | NULL    |       |
| marks | tinyint     | YES  |     | 0       |       |
+-------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> insert into uSquare values(1,"Meenu",1,-12);
ERROR 3819 (HY000): Check constraint 'uSquare_chk_1' is violated.
mysql> insert into uSquare values(1,"Meenu",1,12);
Query OK, 1 row affected (0.01 sec)

mysql> insert into uSquare values(2,"Meenu",2,12);
Query OK, 1 row affected (0.01 sec)

mysql> insert into United(roll,name,marks) values(1,"Meenu",100);
Query OK, 1 row affected (0.01 sec)

mysql> select * from United;
+------+-------+------+-------+
| roll | name  | id   | marks |
+------+-------+------+-------+
|    1 | Meenu | NULL |   100 |
+------+-------+------+-------+
1 row in set (0.00 sec)

mysql> select * from uSquare;
+----+-------+------+-----+
| id | name  | roll | age |
+----+-------+------+-----+
|  1 | Meenu |    1 |  12 |
|  2 | Meenu |    2 |  12 |
+----+-------+------+-----+
2 rows in set (0.00 sec)

mysql> insert into United(roll,name,marks) values(4,"Meenu",100);
Query OK, 1 row affected (0.01 sec)


mysql> insert into United values(6,"Meenu",1,100);
Query OK, 1 row affected (0.00 sec)


mysql> alter table uSquare change roll roll tinyint auto_increment;
Query OK, 2 rows affected (0.10 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> insert into uSquare(id,name,age) values(5,"Pradeep",12);
Query OK, 1 row affected (0.01 sec)

mysql> select * from United;
+------+-------+------+-------+
| roll | name  | id   | marks |
+------+-------+------+-------+
|    1 | Meenu | NULL |   100 |
|    4 | Meenu | NULL |   100 |
|    6 | Meenu |    1 |   100 |
+------+-------+------+-------+
3 rows in set (0.00 sec)

mysql> select * from uSquare;
+----+---------+------+-----+
| id | name    | roll | age |
+----+---------+------+-----+
|  1 | Meenu   |    1 |  12 |
|  2 | Meenu   |    2 |  12 |
|  5 | Pradeep |    3 |  12 |
+----+---------+------+-----+
3 rows in set (0.00 sec)

mysql> delete from uSquare where roll=3;
Query OK, 1 row affected (0.00 sec)

mysql> insert into uSquare(id,name,age) values(6,"Pradeep",12);
Query OK, 1 row affected (0.01 sec)

mysql> select * from uSquare;
+----+---------+------+-----+
| id | name    | roll | age |
+----+---------+------+-----+
|  1 | Meenu   |    1 |  12 |
|  2 | Meenu   |    2 |  12 |
|  6 | Pradeep |    4 |  12 |
+----+---------+------+-----+
3 rows in set (0.00 sec)

### MySQL Joins Practice

mysql> create database Supply;
Query OK, 1 row affected (0.01 sec)

mysql> use Supply;
Database changed
mysql> create table suppliers(supplier_no varchar(2) primary key,supplier_name varchar(25) unique not null,status smallint default 0,city varchar(20) not null);
Query OK, 0 rows affected (0.05 sec)

mysql> create table items(item_no varchar(2) primary key,item_name varchar(25) unique not null,price tinyint not null check(price>=5));
Query OK, 0 rows affected (0.06 sec)

mysql> create table shipments(supplier_no varchar(2) not null,item_no varchar(2) not null,quantity_supplied tinyint default 0,foreign key(supplier_no) references suppliers(supplier_no),foreign key(item_no) references items(item_no));
Query OK, 0 rows affected (0.06 sec)

mysql> desc suppliers;
+---------------+-------------+------+-----+---------+-------+
| Field         | Type        | Null | Key | Default | Extra |
+---------------+-------------+------+-----+---------+-------+
| supplier_no   | varchar(2)  | NO   | PRI | NULL    |       |
| supplier_name | varchar(25) | NO   | UNI | NULL    |       |
| status        | smallint    | YES  |     | 0       |       |
| city          | varchar(20) | NO   |     | NULL    |       |
+---------------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

mysql> insert into suppliers values("S1","Britannia",10,"Delhi"),("S2","New Bakers",12,"Bangalore");
Query OK, 2 rows affected (0.00 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> insert into suppliers values("S3","Cookz",10,"Delhi"),("S4","Haldiram",12,"Tamil Nadu");
Query OK, 2 rows affected (0.00 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> insert into suppliers values("S5","Parle",30,"Telangana"),("S6","Good Day",32,"Tamil Nadu");
Query OK, 2 rows affected (0.01 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> desc items;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| item_no   | varchar(2)  | NO   | PRI | NULL    |       |
| item_name | varchar(25) | NO   | UNI | NULL    |       |
| price     | tinyint     | NO   |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> insert into items values("I1","Milk",30),("I2","Cake",30),("I3","Bread",10),("I4","Milk Bread",12),("I5","Biscuit",30);
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> desc shipments;
+-------------------+------------+------+-----+---------+-------+
| Field             | Type       | Null | Key | Default | Extra |
+-------------------+------------+------+-----+---------+-------+
| supplier_no       | varchar(2) | NO   | MUL | NULL    |       |
| item_no           | varchar(2) | NO   | MUL | NULL    |       |
| quantity_supplied | tinyint    | YES  |     | 0       |       |
+-------------------+------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> insert into shipments values("S1","I3",30),("S2","I4",30),("S1","I3",10),("S4","I1",12),("S5","I2",30);
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0





