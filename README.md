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
|:--:|:--:|:--:|:--:|:--:|:--:|
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

4 rows in set (0.00 sec)      

## OPERATORS

### ``` SELECT 4+3,4-3,4*3,4/3,4%3; /* ARITHMETIC OPERATORS */ ```


| 4+3 | 4-3 | 4*3 | 4/3    | 4%3  |
|:--:|:--:|:--:|:--:|:--:|
|   7 |   1 |  12 | 1.3333 |    1 |


#### Logical Operators

### ``` SELECT 1 AND 0,1 AND 1,1 AND NULL,0 AND NULL;```


| 1 AND 0 | 1 AND 1 | 1 AND NULL | 0 AND NULL |
|:--:|:--:|:--:|:--|
|       0 |       1 |       NULL |          0 |

1 row in set (0.00 sec)

### ``` SELECT 1 OR 0,1 OR 1,1 OR NULL,0 OR NULL; ```


| 1 OR 0 | 1 OR 1 | 1 OR NULL | 0 OR NULL |
|:--:|:--:|:--:|:--:|
|      1 |      1 |         1 |      NULL |

1 row in set (0.00 sec)


