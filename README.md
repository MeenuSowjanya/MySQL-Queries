# MySQL Queries

### ``` SHOW DATABASES ;```


| Database           |
|:------------------:|
| Supply             |
| document           |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| test               |

7 rows in set (0.00 sec)

### ``` CREATE DATABASE School; ```

##### ``` Query OK, 1 row affected (0.00 sec)```

### ``` USE School; ```

##### ``` Database changed```

### ``` CREATE TABLE students(id TINYINT PRIMARY KEY CHECK(id>0),name VARCHAR(30) NOT NULL,class TINYINT(2) NOT NULL CHECK (class>0));```

##### ``` Query OK, 0 rows affected, 1 warning (0.04 sec)```

### ``` DESC students; ```


| Field | Type        | Null | Key | Default | Extra |
|:--:|:--|--|--|
| id    | tinyint     | NO   | PRI | NULL    |       |
| name  | varchar(30) | NO   |     | NULL    |       |
| class | tinyint     | NO   |     | NULL    |       |

3 rows in set (0.00 sec)

### ``` INSERT INTO students values(1,"Meenu",12);```

#### ```Query OK, 1 row affected (0.00 sec) ```

##### /*After inserting multiple rows :*/

### ``` SELECT * FROM students; ```


| id | name    | class |
|:--:|:--:|:--|
|  1 | Meenu   |    12 |
|  2 | Pradeep |    12 |
|  3 | Rohan   |    12 |
|  4 | Sneha   |    12 |

4 rows in set (0.00 sec)

### ```UPDATE students SET name="Kumar" WHERE id=4;```

#### ```Query OK, 1 row affected (0.01 sec)```

#### ```Rows matched: 1  Changed: 1  Warnings: 0```

##### /*RESULT :*/


| id | name    | class |
|:--:|:--:|:--:|
|  1 | Meenu   |    12 |
|  2 | Pradeep |    12 |
|  3 | Rohan   |    12 |
|  4 | Kumar   |    12 |
+----+---------+-------+
4 rows in set (0.00 sec)      





