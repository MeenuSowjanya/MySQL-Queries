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
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)


