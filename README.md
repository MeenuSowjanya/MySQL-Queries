# MySQL Queries

 ``` SHOW DATABASES ;```


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

 ``` CREATE DATABASE School; ```

##### ``` Query OK, 1 row affected (0.00 sec)```

 ``` USE School; ```

##### ``` Database changed```

 ``` CREATE TABLE students(id TINYINT PRIMARY KEY CHECK(id>0),name VARCHAR(30) NOT NULL,class TINYINT(2) NOT NULL CHECK (class>0));```

 ``` Query OK, 0 rows affected, 1 warning (0.04 sec)```

 ``` DESC students; ```


| Field | Type        | Null | Key | Default | Extra |
|:--:|:--:|:--:|:--:|:--:|:--:|
| id    | tinyint     | NO   | PRI | NULL    |       |
| name  | varchar(30) | NO   |     | NULL    |       |
| class | tinyint     | NO   |     | NULL    |       |

3 rows in set (0.00 sec)

``` INSERT INTO students values(1,"Meenu",12);```

#### ```Query OK, 1 row affected (0.00 sec) ```

##### /*After inserting multiple rows :*/

``` SELECT * FROM students; ```


| id | name    | class |
|:--:|:--:|:--|
|  1 | Meenu   |    12 |
|  2 | Pradeep |    12 |
|  3 | Rohan   |    12 |
|  4 | Sneha   |    12 |

4 rows in set (0.00 sec)

 ```UPDATE students SET name="Kumar" WHERE id=4;```

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

 ``` SELECT 4+3,4-3,4*3,4/3,4%3; /* ARITHMETIC OPERATORS */ ```


| 4+3 | 4-3 | 4*3 | 4/3    | 4%3  |
|:--:|:--:|:--:|:--:|:--:|
|   7 |   1 |  12 | 1.3333 |    1 |


### Logical Operators

 ``` SELECT 1 AND 0,1 AND 1,1 AND NULL,0 AND NULL;```


| 1 AND 0 | 1 AND 1 | 1 AND NULL | 0 AND NULL |
|:--:|:--:|:--:|:--|
|       0 |       1 |       NULL |          0 |

1 row in set (0.00 sec)

 ``` SELECT 1 OR 0,1 OR 1,1 OR NULL,0 OR NULL; ```


| 1 OR 0 | 1 OR 1 | 1 OR NULL | 0 OR NULL |
|:--:|:--:|:--:|:--:|
|      1 |      1 |         1 |      NULL |

1 row in set (0.00 sec)

 ``` SELECT 1 XOR 0,1 XOR 1,0 OR 0,0 XOR NULL,1 XOR NULL,1 XOR 1 XOR 1; ```


| 1 XOR 0 | 1 XOR 1 | 0 OR 0 | 0 XOR NULL | 1 XOR NULL | 1 XOR 1 XOR 1 |
|:--:|:--:|:--:|:--:|:--:|:--:|
|       1 |       0 |      0 |       NULL |       NULL |             1 |

1 row in set (0.00 sec)

 ``` SELECT NOT((1 OR 0) AND (1 XOR 1)); ```


| NOT((1 OR 0) AND (1 XOR 1)) |
|:--:|
|                           1 |

1 row in set (0.00 sec)

 ``` SELECT * FROM students WHERE name LIKE("R%") OR name LIKE("%P") OR name LIKE("ME__U%"); ```


| id | name    | class |
|:--:|:--:|:--:|
|  1 | Meenu   |    12 |
|  2 | Pradeep |    12 |
|  3 | Rohan   |    12 |

3 rows in set (0.00 sec)

 ```SELECT * FROM students WHERE id> ANY(SELECT marks FROM mark_list);```

Empty set (0.00 sec)

 ```SELECT * FROM students WHERE id< ANY(SELECT marks FROM mark_list);```


| id | name    | class |
|:--:|:--:|:--:|
|  1 | Meenu   |    12 |
|  2 | Pradeep |    12 |
|  3 | Rohan   |    12 |
|  4 | Kumar   |    12 |

4 rows in set (0.00 sec)

 ``` SELECT * FROM students WHERE id IN(SELECT marks FROM mark_list); ```
 
Empty set (0.00 sec)

 ``` SELECT * FROM students WHERE id NOT IN(SELECT marks FROM mark_list); ```


| id | name    | class |
|:--:|:--:|:--:|
|  1 | Meenu   |    12 |
|  2 | Pradeep |    12 |
|  3 | Rohan   |    12 |
|  4 | Kumar   |    12 |

4 rows in set (0.00 sec)

 ``` SELECT * FROM students WHERE id< ALL(SELECT marks FROM mark_list); ```

| id | name    | class |
|:--:|:--:|:--:|
|  1 | Meenu   |    12 |
|  2 | Pradeep |    12 |
|  3 | Rohan   |    12 |
|  4 | Kumar   |    12 |

4 rows in set (0.00 sec)

``` SELECT * FROM students WHERE EXISTS(SELECT name FROM mark_list WHERE name LIKE("P%")); ```


| id | name    | class |
|:--:|:--:|:--:|
|  2 | Pradeep |    12 |

1 row in set (0.00 sec)

 ``` SELECT * FROM students WHERE NOT EXISTS(SELECT name FROM mark_list WHERE name LIKE("P%")); ```


| id | name  | class |
|:--:|:--:|:--:|
|  1 | Meenu |    12 |
|  3 | Rohan |    12 |
|  4 | Kumar |    12 |

3 rows in set (0.00 sec)

### RELATIONAL OPERATORS

 ``` SELECT 1=2,1=1; ```


| 1=2 | 1=1 |
|:--:|:--:|
|   0 |   1 |

1 row in set (0.00 sec)

``` SELECT 1>2,1<1,1<>2,1!=1,1<=>1,1<=2,2>=4; ```


| 1>2 | 1<1 | 1<>2 | 1!=1 | 1<=>1 | 1<=2 | 2>=4 |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|   0 |   0 |    1 |    0 |     1 |    1 |    0 |

1 row in set (0.00 sec)

``` SELECT * FROM students WHERE id BETWEEN 1 AND 3; ```


| id | name    | class |
|:--:|:--:|:--:|
|  1 | Meenu   |    12 |
|  2 | Pradeep |    12 |
|  3 | Rohan   |    12 |

3 rows in set (0.00 sec)

``` SELECT * FROM students WHERE id NOT BETWEEN 1 AND 3; ```


| id | name  | class |
|:--:|:--:|:--:|
|  4 | Kumar |    12 |

1 row in set (0.00 sec)

``` SELECT COALESCE(NULL,NULL,10,NULL,1),GREATEST(1.00787918,9.0939279,1,2,1.2827392793),LEAST(1.3923920,1.2792883,0.487249,0.7293983,6); ```


| COALESCE(NULL,NULL,10,NULL,1) | GREATEST(1.00787918,9.0939279,1,2,1.2827392793) | LEAST(1.3923920,1.2792883,0.487249,0.7293983,6) |
|:--:|:--:|:--:|
|                            10 |                                    9.0939279000 |                                       0.4872490 |

1 row in set (0.00 sec)

``` SELECT 1 IN (1,2,76283728,"MEENU"), "PRADEEP" NOT IN ("ROHAN","SNEHA","MEENU"); ```


| 1 IN (1,2,76283728,"MEENU") | "PRADEEP" NOT IN ("ROHAN","SNEHA","MEENU") |
|:--:|:--:|:--:|
|                           1 |                                          1 |

1 row in set (0.00 sec)

``` SELECT 1 IS NOT UNKNOWN, 0 IS NOT UNKNOWN, NULL IS NOT UNKNOWN; ```


| 1 IS NOT UNKNOWN | 0 IS NOT UNKNOWN | NULL IS NOT UNKNOWN |
|:--:|:--:|:--:|
|                1 |                1 |                   0 |

1 row in set (0.00 sec)

``` SELECT 1 IS NULL, 0 IS NULL, NULL IS NOT NULL; ```


| 1 IS NULL | 0 IS NULL | NULL IS NOT NULL |
|:--:|:--:|:--:|
|         0 |         0 |                0 |

1 row in set (0.00 sec)

``` SELECT ISNULL(1+1),ISNULL(1/0); ```


| ISNULL(1+1) | ISNULL(1/0) |
|:--:|:--:|
|           0 |           1 |

1 row in set, 1 warning (0.00 sec)

## ALTER COMMANDS

```ALTER TABLE students MODIFY name varchar(30),ADD COLUMN blood_group varchar(2) NOT NULL AFTER name;```


