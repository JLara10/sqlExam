# sqlExam
select * from movies;
+-------------------+---------+-------------+------------+--------+
| Title             | Runtime | Genre       | IMDB_SCORE | Rating |
+-------------------+---------+-------------+------------+--------+
| Howard the Duck   |     110 | Sci-Fi      |        4.6 | PG     |
| Lavalantula       |      83 | Horror      |        4.7 | TV-14  |
| Starship Troopers |     129 | Sci-Fi      |        7.2 | PG-13  |
| Waltz With Bashir |      90 | Documentary |        8.0 | R      |
| Spaceballs        |      96 | Comedy      |        7.1 | PG     |
| Monster Inc.      |      92 | Animation   |        8.1 | G      |
+-------------------+---------+-------------+------------+--------+
6 rows in set (0.49 sec)

mysql> Insert Into (Title, Runtime, Genre, IMDB_SCORE, Rating) Values
    -> ('Transformers', 143, 'Action', 5.1, 'PG-13'),
    -> ('American Sniper', 133, 'Action', 8.2, 'R');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '(Title, Runtime, Genre, IMDB_SCORE, Rating) Values
('Transformers', 143, 'Action' at line 1
mysql> Insert Into movies (Title, Runtime, Genre, IMDB_SCORE, Rating) Values                                                                            -> ('Transformers', 143, 'Action', 5.1, 'PG-13'),                                                                                                   -> ('American Sniper', 133, 'Action', 8.2, 'R');                                                                                                Query OK, 2 rows affected (0.30 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> select * from movies;
+-------------------+---------+-------------+------------+--------+
| Title             | Runtime | Genre       | IMDB_SCORE | Rating |
+-------------------+---------+-------------+------------+--------+
| Howard the Duck   |     110 | Sci-Fi      |        4.6 | PG     |
| Lavalantula       |      83 | Horror      |        4.7 | TV-14  |
| Starship Troopers |     129 | Sci-Fi      |        7.2 | PG-13  |
| Waltz With Bashir |      90 | Documentary |        8.0 | R      |
| Spaceballs        |      96 | Comedy      |        7.1 | PG     |
| Monster Inc.      |      92 | Animation   |        8.1 | G      |
| Transformers      |     143 | Action      |        5.1 | PG-13  |
| American Sniper   |     133 | Action      |        8.2 | R      |
+-------------------+---------+-------------+------------+--------+
8 rows in set (0.00 sec)

mysql> SELECt * from movies Where Genre = 'Sci-Fi';
+-------------------+---------+--------+------------+--------+
| Title             | Runtime | Genre  | IMDB_SCORE | Rating |
+-------------------+---------+--------+------------+--------+
| Howard the Duck   |     110 | Sci-Fi |        4.6 | PG     |
| Starship Troopers |     129 | Sci-Fi |        7.2 | PG-13  |
+-------------------+---------+--------+------------+--------+
2 rows in set (0.06 sec)

mysql> select * from movies where IMDB_SCORE >= 6.5;
+-------------------+---------+-------------+------------+--------+
| Title             | Runtime | Genre       | IMDB_SCORE | Rating |
+-------------------+---------+-------------+------------+--------+
| Starship Troopers |     129 | Sci-Fi      |        7.2 | PG-13  |
| Waltz With Bashir |      90 | Documentary |        8.0 | R      |
| Spaceballs        |      96 | Comedy      |        7.1 | PG     |
| Monster Inc.      |      92 | Animation   |        8.1 | G      |
| American Sniper   |     133 | Action      |        8.2 | R      |
+-------------------+---------+-------------+------------+--------+
5 rows in set (0.03 sec)

mysql> select * from movies Where Runtime < 100 AND rating = 'G' OR rating= 'PG';
+-----------------+---------+-----------+------------+--------+
| Title           | Runtime | Genre     | IMDB_SCORE | Rating |
+-----------------+---------+-----------+------------+--------+
| Howard the Duck |     110 | Sci-Fi    |        4.6 | PG     |
| Spaceballs      |      96 | Comedy    |        7.1 | PG     |
| Monster Inc.    |      92 | Animation |        8.1 | G      |
+-----------------+---------+-----------+------------+--------+
3 rows in set (0.06 sec)

mysql> select AVG(Runtime) AS AVG_Runtime from movies Where IMDB_SCORE < 7.5 Group By Genre;
+-------------+
| AVG_Runtime |
+-------------+
|    119.5000 |
|     83.0000 |
|     96.0000 |
|    143.0000 |
+-------------+
4 rows in set (0.12 sec)

mysql> select Genre, AVG(Runtime) AS AVG_Runtime from movies Where IMDB_SCORE < 7.5 Group By Genre;
+--------+-------------+
| Genre  | AVG_Runtime |
+--------+-------------+
| Sci-Fi |    119.5000 |
| Horror |     83.0000 |
| Comedy |     96.0000 |
| Action |    143.0000 |
+--------+-------------+
4 rows in set (0.02 sec)

mysql> UPDATE movies SET Rating = 'R' Where Title = Starship Troppers;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'Troppers' at line 1
mysql> UPDATE movies SET Rating = 'R' Where Title = 'Starship Troppers';
Query OK, 0 rows affected (0.04 sec)
Rows matched: 0  Changed: 0  Warnings: 0

mysql> select * from movies;
+-------------------+---------+-------------+------------+--------+
| Title             | Runtime | Genre       | IMDB_SCORE | Rating |
+-------------------+---------+-------------+------------+--------+
| Howard the Duck   |     110 | Sci-Fi      |        4.6 | PG     |
| Lavalantula       |      83 | Horror      |        4.7 | TV-14  |
| Starship Troopers |     129 | Sci-Fi      |        7.2 | PG-13  |
| Waltz With Bashir |      90 | Documentary |        8.0 | R      |
| Spaceballs        |      96 | Comedy      |        7.1 | PG     |
| Monster Inc.      |      92 | Animation   |        8.1 | G      |
| Transformers      |     143 | Action      |        5.1 | PG-13  |
| American Sniper   |     133 | Action      |        8.2 | R      |
+-------------------+---------+-------------+------------+--------+
8 rows in set (0.01 sec)

mysql> UPDATE movies SET Rating = 'R' Where Title = 'Starship Troopers';
Query OK, 1 row affected (0.07 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from movies;
+-------------------+---------+-------------+------------+--------+
| Title             | Runtime | Genre       | IMDB_SCORE | Rating |
+-------------------+---------+-------------+------------+--------+
| Howard the Duck   |     110 | Sci-Fi      |        4.6 | PG     |
| Lavalantula       |      83 | Horror      |        4.7 | TV-14  |
| Starship Troopers |     129 | Sci-Fi      |        7.2 | R      |
| Waltz With Bashir |      90 | Documentary |        8.0 | R      |
| Spaceballs        |      96 | Comedy      |        7.1 | PG     |
| Monster Inc.      |      92 | Animation   |        8.1 | G      |
| Transformers      |     143 | Action      |        5.1 | PG-13  |
| American Sniper   |     133 | Action      |        8.2 | R      |
+-------------------+---------+-------------+------------+--------+
8 rows in set (0.00 sec)

mysql> select ID, Rating from movies where Genre In ('Horror', 'Documentary');
ERROR 1054 (42S22): Unknown column 'ID' in 'field list'
mysql> ALTER TABLE movies ADD ID INT; 
Query OK, 0 rows affected (0.62 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select * from movies;
+-------------------+---------+-------------+------------+--------+------+
| Title             | Runtime | Genre       | IMDB_SCORE | Rating | ID   |
+-------------------+---------+-------------+------------+--------+------+
| Howard the Duck   |     110 | Sci-Fi      |        4.6 | PG     | NULL |
| Lavalantula       |      83 | Horror      |        4.7 | TV-14  | NULL |
| Starship Troopers |     129 | Sci-Fi      |        7.2 | R      | NULL |
| Waltz With Bashir |      90 | Documentary |        8.0 | R      | NULL |
| Spaceballs        |      96 | Comedy      |        7.1 | PG     | NULL |
| Monster Inc.      |      92 | Animation   |        8.1 | G      | NULL |
| Transformers      |     143 | Action      |        5.1 | PG-13  | NULL |
| American Sniper   |     133 | Action      |        8.2 | R      | NULL |
+-------------------+---------+-------------+------------+--------+------+
8 rows in set (0.02 sec)

mysql> INSERT INTO movies Values (1, 2, 3, 4, 5, 6, 7, 8); 
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> INSERT INTO movies Values 
    -> (1),
    -> (2),
    -> (3),
    -> (4),
    -> (5),
    -> (6),
    -> (7),
    -> (8);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> ALTER TABLE movies DROP COLUMN ID;
Query OK, 0 rows affected (0.19 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select * from movies;
+-------------------+---------+-------------+------------+--------+
| Title             | Runtime | Genre       | IMDB_SCORE | Rating |
+-------------------+---------+-------------+------------+--------+
| Howard the Duck   |     110 | Sci-Fi      |        4.6 | PG     |
| Lavalantula       |      83 | Horror      |        4.7 | TV-14  |
| Starship Troopers |     129 | Sci-Fi      |        7.2 | R      |
| Waltz With Bashir |      90 | Documentary |        8.0 | R      |
| Spaceballs        |      96 | Comedy      |        7.1 | PG     |
| Monster Inc.      |      92 | Animation   |        8.1 | G      |
| Transformers      |     143 | Action      |        5.1 | PG-13  |
| American Sniper   |     133 | Action      |        8.2 | R      |
+-------------------+---------+-------------+------------+--------+
8 rows in set (0.00 sec)

mysql> ALTER TABLE movies ADD PRIMARY KEY (ID);
ERROR 1072 (42000): Key column 'ID' doesn't exist in table
mysql> ALTER TABLE movies ADD ID INT PRIMARY KEY;
ERROR 1062 (23000): Duplicate entry '0' for key 'movies.PRIMARY'
mysql> ALTER TABLE movies DROP PRIMARY KEY;
ERROR 1091 (42000): Can't DROP 'PRIMARY'; check that column/key exists
mysql> select * from movies;
+-------------------+---------+-------------+------------+--------+
| Title             | Runtime | Genre       | IMDB_SCORE | Rating |
+-------------------+---------+-------------+------------+--------+
| Howard the Duck   |     110 | Sci-Fi      |        4.6 | PG     |
| Lavalantula       |      83 | Horror      |        4.7 | TV-14  |
| Starship Troopers |     129 | Sci-Fi      |        7.2 | R      |
| Waltz With Bashir |      90 | Documentary |        8.0 | R      |
| Spaceballs        |      96 | Comedy      |        7.1 | PG     |
| Monster Inc.      |      92 | Animation   |        8.1 | G      |
| Transformers      |     143 | Action      |        5.1 | PG-13  |
| American Sniper   |     133 | Action      |        8.2 | R      |
+-------------------+---------+-------------+------------+--------+
8 rows in set (0.01 sec)

mysql> ALTER TABLE movies ADD ID INT AUTO_INCREMENT;
ERROR 1075 (42000): Incorrect table definition; there can be only one auto column and it must be defined as a key
mysql> ALTER TABLE movies ADD ID INT AUTO_INCREMENT PRIMARY KEY;
Query OK, 0 rows affected (0.29 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> select * from movies; 
+-------------------+---------+-------------+------------+--------+----+
| Title             | Runtime | Genre       | IMDB_SCORE | Rating | ID |
+-------------------+---------+-------------+------------+--------+----+
| Howard the Duck   |     110 | Sci-Fi      |        4.6 | PG     |  1 |
| Lavalantula       |      83 | Horror      |        4.7 | TV-14  |  2 |
| Starship Troopers |     129 | Sci-Fi      |        7.2 | R      |  3 |
| Waltz With Bashir |      90 | Documentary |        8.0 | R      |  4 |
| Spaceballs        |      96 | Comedy      |        7.1 | PG     |  5 |
| Monster Inc.      |      92 | Animation   |        8.1 | G      |  6 |
| Transformers      |     143 | Action      |        5.1 | PG-13  |  7 |
| American Sniper   |     133 | Action      |        8.2 | R      |  8 |
+-------------------+---------+-------------+------------+--------+----+
8 rows in set (0.00 sec)

mysql> select ID, Rating from movies Where genre IN ('Horror', 'Documentary');
+----+--------+
| ID | Rating |
+----+--------+
|  2 | TV-14  |
|  4 | R      |
+----+--------+
2 rows in set (0.02 sec)

mysql> select AVG(IMDB_SCORE0, MAX(IMDB_SCORE), MIN(IMDB_SCORE) from movies Group by Rating;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ', MAX(IMDB_SCORE), MIN(IMDB_SCORE) from movies Group by Rating' at line 1
mysql> select AVG(IMDB_SCORE), MAX(IMDB_SCORE), MIN(IMDB_SCORE) from movies Group by Rating;
+-----------------+-----------------+-----------------+
| AVG(IMDB_SCORE) | MAX(IMDB_SCORE) | MIN(IMDB_SCORE) |
+-----------------+-----------------+-----------------+
|         5.85000 |             7.1 |             4.6 |
|         4.70000 |             4.7 |             4.7 |
|         7.80000 |             8.2 |             7.2 |
|         8.10000 |             8.1 |             8.1 |
|         5.10000 |             5.1 |             5.1 |
+-----------------+-----------------+-----------------+
5 rows in set (0.08 sec)

mysql> select Rating, AVG(IMDB_SCORE), MAX(IMDB_SCORE), MIN(IMDB_SCORE) from movies Group by Rating;
+--------+-----------------+-----------------+-----------------+
| Rating | AVG(IMDB_SCORE) | MAX(IMDB_SCORE) | MIN(IMDB_SCORE) |
+--------+-----------------+-----------------+-----------------+
| PG     |         5.85000 |             7.1 |             4.6 |
| TV-14  |         4.70000 |             4.7 |             4.7 |
| R      |         7.80000 |             8.2 |             7.2 |
| G      |         8.10000 |             8.1 |             8.1 |
| PG-13  |         5.10000 |             5.1 |             5.1 |
+--------+-----------------+-----------------+-----------------+
5 rows in set (0.01 sec)

mysql> Select rating FROM movies GROUP BY Rating HAVING COUNT(*) >1;
+--------+
| rating |
+--------+
| PG     |
| R      |
+--------+
2 rows in set (0.14 sec)

mysql> DELETE FROM movies WHERE Rating = 'R';
Query OK, 3 rows affected (0.13 sec)

mysql> select * from movies;
+-----------------+---------+-----------+------------+--------+----+
| Title           | Runtime | Genre     | IMDB_SCORE | Rating | ID |
+-----------------+---------+-----------+------------+--------+----+
| Howard the Duck |     110 | Sci-Fi    |        4.6 | PG     |  1 |
| Lavalantula     |      83 | Horror    |        4.7 | TV-14  |  2 |
| Spaceballs      |      96 | Comedy    |        7.1 | PG     |  5 |
| Monster Inc.    |      92 | Animation |        8.1 | G      |  6 |
| Transformers    |     143 | Action    |        5.1 | PG-13  |  7 |
+-----------------+---------+-----------+------------+--------+----+
5 rows in set (0.03 sec)
mysql> drop table movies;
Query OK, 0 rows affected (0.22 sec)

mysql> drop database movies_db;
Query OK, 0 rows affected (0.12 sec)
mysql> 
