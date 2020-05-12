# MySQL_Logical_Operators

## Not Equal
```

mysql> SELECT title,author_fname,author_lname FROM books;
+-----------------------------------------------------+--------------+----------------+
| title                                               | author_fname | author_lname   |
+-----------------------------------------------------+--------------+----------------+
| The Namesake                                        | Jhumpa       | Lahiri         |
| Norse Mythology                                     | Neil         | Gaiman         |
| American Gods                                       | Neil         | Gaiman         |
| Interpreter of Maladies                             | Jhumpa       | Lahiri         |
| A Hologram for the King: A Novel                    | Dave         | Eggers         |
| The Circle                                          | Dave         | Eggers         |
| The Amazing Adventures of Kavalier & Clay           | Michael      | Chabon         |
| Just Kids                                           | Patti        | Smith          |
| A Heartbreaking Work of Staggering Genius           | Dave         | Eggers         |
| Coraline                                            | Neil         | Gaiman         |
| What We Talk About When We Talk About Love: Stories | Raymond      | Carver         |
| Where I'm Calling From: Selected Stories            | Raymond      | Carver         |
| White Noise                                         | Don          | DeLillo        |
| Cannery Row                                         | John         | Steinbeck      |
| Oblivion: Stories                                   | David        | Foster Wallace |
| Consider the Lobster                                | David        | Foster Wallace |
| 10% Happier                                         | Dan          | Harris         |
| fake_book                                           | Freida       | Harris         |
| Lincoln In The Bardo                                | George       | Saunders       |
+-----------------------------------------------------+--------------+----------------+
19 rows in set (0.00 sec)
Database changed
mysql> SELECT title FROM books WHERE released_year = 2017;
+----------------------+
| title                |
+----------------------+
| Lincoln In The Bardo |
+----------------------+
1 row in set (0.00 sec)

mysql> SELECT title FROM books WHERE released_year != 2017;
+-----------------------------------------------------+
| title                                               |
+-----------------------------------------------------+
| The Namesake                                        |
| Norse Mythology                                     |
| American Gods                                       |
| Interpreter of Maladies                             |
| A Hologram for the King: A Novel                    |
| The Circle                                          |
| The Amazing Adventures of Kavalier & Clay           |
| Just Kids                                           |
| A Heartbreaking Work of Staggering Genius           |
| Coraline                                            |
| What We Talk About When We Talk About Love: Stories |
| Where I'm Calling From: Selected Stories            |
| White Noise                                         |
| Cannery Row                                         |
| Oblivion: Stories                                   |
| Consider the Lobster                                |
| 10% Happier                                         |
| fake_book                                           |
+-----------------------------------------------------+
18 rows in set (0.00 sec)

mysql> SELECT title, author_lname FROM books WHERE author_lname != 'Harris';
+-----------------------------------------------------+----------------+
| title                                               | author_lname   |
+-----------------------------------------------------+----------------+
| The Namesake                                        | Lahiri         |
| Norse Mythology                                     | Gaiman         |
| American Gods                                       | Gaiman         |
| Interpreter of Maladies                             | Lahiri         |
| A Hologram for the King: A Novel                    | Eggers         |
| The Circle                                          | Eggers         |
| The Amazing Adventures of Kavalier & Clay           | Chabon         |
| Just Kids                                           | Smith          |
| A Heartbreaking Work of Staggering Genius           | Eggers         |
| Coraline                                            | Gaiman         |
| What We Talk About When We Talk About Love: Stories | Carver         |
| Where I'm Calling From: Selected Stories            | Carver         |
| White Noise                                         | DeLillo        |
| Cannery Row                                         | Steinbeck      |
| Oblivion: Stories                                   | Foster Wallace |
| Consider the Lobster                                | Foster Wallace |
| Lincoln In The Bardo                                | Saunders       |
+-----------------------------------------------------+----------------+
17 rows in set (0.00 sec)
```
## Not Like
```

mysql> SELECT title FROM books WHERE title LIKE 'W';
Empty set (0.00 sec)

mysql> SELECT title FROM books WHERE title LIKE 'W%';
+-----------------------------------------------------+
| title                                               |
+-----------------------------------------------------+
| What We Talk About When We Talk About Love: Stories |
| Where I'm Calling From: Selected Stories            |
| White Noise                                         |
+-----------------------------------------------------+
3 rows in set (0.00 sec)

mysql> SELECT title FROM books WHERE title LIKE '%W%';
+-----------------------------------------------------+
| title                                               |
+-----------------------------------------------------+
| A Heartbreaking Work of Staggering Genius           |
| What We Talk About When We Talk About Love: Stories |
| Where I'm Calling From: Selected Stories            |
| White Noise                                         |
| Cannery Row                                         |
+-----------------------------------------------------+
5 rows in set (0.00 sec)

mysql> SELECT title FROM books WHERE title LIKE 'W%';
+-----------------------------------------------------+
| title                                               |
+-----------------------------------------------------+
| What We Talk About When We Talk About Love: Stories |
| Where I'm Calling From: Selected Stories            |
| White Noise                                         |
+-----------------------------------------------------+
3 rows in set (0.00 sec)

mysql> SELECT title FROM books WHERE title NOT LIKE 'W%';
+-------------------------------------------+
| title                                     |
+-------------------------------------------+
| The Namesake                              |
| Norse Mythology                           |
| American Gods                             |
| Interpreter of Maladies                   |
| A Hologram for the King: A Novel          |
| The Circle                                |
| The Amazing Adventures of Kavalier & Clay |
| Just Kids                                 |
| A Heartbreaking Work of Staggering Genius |
| Coraline                                  |
| Cannery Row                               |
| Oblivion: Stories                         |
| Consider the Lobster                      |
| 10% Happier                               |
| fake_book                                 |
| Lincoln In The Bardo                      |
+-------------------------------------------+
16 rows in set (0.00 sec)
```
## Greater Than, Less Than
```
mysql> SELECT title, released_year FROM books ORDER BY released_year;
+-----------------------------------------------------+---------------+
| title                                               | released_year |
+-----------------------------------------------------+---------------+
| Cannery Row                                         |          1945 |
| What We Talk About When We Talk About Love: Stories |          1981 |
| White Noise                                         |          1985 |
| Where I'm Calling From: Selected Stories            |          1989 |
| Interpreter of Maladies                             |          1996 |
| The Amazing Adventures of Kavalier & Clay           |          2000 |
| fake_book                                           |          2001 |
| American Gods                                       |          2001 |
| A Heartbreaking Work of Staggering Genius           |          2001 |
| Coraline                                            |          2003 |
| The Namesake                                        |          2003 |
| Oblivion: Stories                                   |          2004 |
| Consider the Lobster                                |          2005 |
| Just Kids                                           |          2010 |
| A Hologram for the King: A Novel                    |          2012 |
| The Circle                                          |          2013 |
| 10% Happier                                         |          2014 |
| Norse Mythology                                     |          2016 |
| Lincoln In The Bardo                                |          2017 |
+-----------------------------------------------------+---------------+
19 rows in set (0.03 sec)

mysql> SELECT
    ->   title,
    ->   released_year
    -> FROM books
    -> WHERE released_year > 2000
    -> ORDER BY released_year;
+-------------------------------------------+---------------+
| title                                     | released_year |
+-------------------------------------------+---------------+
| American Gods                             |          2001 |
| A Heartbreaking Work of Staggering Genius |          2001 |
| fake_book                                 |          2001 |
| The Namesake                              |          2003 |
| Coraline                                  |          2003 |
| Oblivion: Stories                         |          2004 |
| Consider the Lobster                      |          2005 |
| Just Kids                                 |          2010 |
| A Hologram for the King: A Novel          |          2012 |
| The Circle                                |          2013 |
| 10% Happier                               |          2014 |
| Norse Mythology                           |          2016 |
| Lincoln In The Bardo                      |          2017 |
+-------------------------------------------+---------------+
13 rows in set (0.05 sec)

mysql> SELECT
    ->   title,
    ->   released_year
    -> FROM books
    -> WHERE released_year >= 2000
    -> ORDER BY released_year;
+-------------------------------------------+---------------+
| title                                     | released_year |
+-------------------------------------------+---------------+
| The Amazing Adventures of Kavalier & Clay |          2000 |
| American Gods                             |          2001 |
| A Heartbreaking Work of Staggering Genius |          2001 |
| fake_book                                 |          2001 |
| The Namesake                              |          2003 |
| Coraline                                  |          2003 |
| Oblivion: Stories                         |          2004 |
| Consider the Lobster                      |          2005 |
| Just Kids                                 |          2010 |
| A Hologram for the King: A Novel          |          2012 |
| The Circle                                |          2013 |
| 10% Happier                               |          2014 |
| Norse Mythology                           |          2016 |
| Lincoln In The Bardo                      |          2017 |
+-------------------------------------------+---------------+
14 rows in set (0.00 sec)

mysql> SELECT title, stock_quantity FROM books WHERE stock_quantity >= 100;
+-------------------------------------------+----------------+
| title                                     | stock_quantity |
+-------------------------------------------+----------------+
| A Hologram for the King: A Novel          |            154 |
| A Heartbreaking Work of Staggering Genius |            104 |
| Coraline                                  |            100 |
| Oblivion: Stories                         |            172 |
| fake_book                                 |            287 |
| Lincoln In The Bardo                      |           1000 |
+-------------------------------------------+----------------+
6 rows in set (0.00 sec)

mysql> SELECT 99 > 1;
+--------+
| 99 > 1 |
+--------+
|      1 |
+--------+
1 row in set (0.01 sec)

mysql>
mysql> SELECT 99 > 567;
+----------+
| 99 > 567 |
+----------+
|        0 |
+----------+
1 row in set (0.00 sec)
```
## AND (&&), OR (||)
```
mysql> SELECT
    ->   title,
    ->   author_lname,
    ->   released_year
    -> FROM books
    -> WHERE author_lname = 'Eggers'
    -> AND released_year > 2010;
+----------------------------------+--------------+---------------+
| title                            | author_lname | released_year |
+----------------------------------+--------------+---------------+
| A Hologram for the King: A Novel | Eggers       |          2012 |
| The Circle                       | Eggers       |          2013 |
+----------------------------------+--------------+---------------+
2 rows in set (0.01 sec)

mysql> SELECT 1 < 5 && 7 = 9;
+----------------+
| 1 < 5 && 7 = 9 |
+----------------+
|              0 |
+----------------+
1 row in set (0.00 sec)

mysql> SELECT -10 > -20 && 0 <= 0;
+---------------------+
| -10 > -20 && 0 <= 0 |
+---------------------+
|                   1 |
+---------------------+
1 row in set (0.01 sec)

mysql> SELECT
    ->   title,
    ->   author_fname,
    ->   author_lname,
    ->   released_year,
    ->   stock_quantity,
    ->   pages
    -> FROM books
    -> WHERE author_lname = 'Eggers'
    -> AND released_year > 2010
    -> AND title LIKE '%novel%';
+----------------------------------+--------------+--------------+---------------+----------------+-------+
| title                            | author_fname | author_lname | released_year | stock_quantity | pages |
+----------------------------------+--------------+--------------+---------------+----------------+-------+
| A Hologram for the King: A Novel | Dave         | Eggers       |          2012 |            154 |   352 |
+----------------------------------+--------------+--------------+---------------+----------------+-------+
1 row in set (0.00 sec)

mysql> SELECT
    ->     title,
    ->     author_lname,
    ->     released_year
    -> FROM books
    -> WHERE author_lname='Eggers' || released_year > 2010;
+-------------------------------------------+--------------+---------------+
| title                                     | author_lname | released_year |
+-------------------------------------------+--------------+---------------+
| Norse Mythology                           | Gaiman       |          2016 |
| A Hologram for the King: A Novel          | Eggers       |          2012 |
| The Circle                                | Eggers       |          2013 |
| A Heartbreaking Work of Staggering Genius | Eggers       |          2001 |
| 10% Happier                               | Harris       |          2014 |
| Lincoln In The Bardo                      | Saunders     |          2017 |
+-------------------------------------------+--------------+---------------+
6 rows in set (0.00 sec)

mysql> SELECT title,
    ->        author_lname,
    ->        released_year,
    ->        stock_quantity
    -> FROM   books
    -> WHERE  author_lname = 'Eggers'
    ->               || released_year > 2010
    -> OR     stock_quantity > 100;
+-------------------------------------------+----------------+---------------+----------------+
| title                                     | author_lname   | released_year | stock_quantity |
+-------------------------------------------+----------------+---------------+----------------+
| Norse Mythology                           | Gaiman         |          2016 |             43 |
| A Hologram for the King: A Novel          | Eggers         |          2012 |            154 |
| The Circle                                | Eggers         |          2013 |             26 |
| A Heartbreaking Work of Staggering Genius | Eggers         |          2001 |            104 |
| Oblivion: Stories                         | Foster Wallace |          2004 |            172 |
| 10% Happier                               | Harris         |          2014 |             29 |
| fake_book                                 | Harris         |          2001 |            287 |
| Lincoln In The Bardo                      | Saunders       |          2017 |           1000 |
+-------------------------------------------+----------------+---------------+----------------+
8 rows in set (0.00 sec)
```

## Between
```
mysql> SELECT
    ->   title,
    ->   released_year
    -> FROM books
    -> WHERE released_year >= 2004
    -> AND released_year <= 2015;
+----------------------------------+---------------+
| title                            | released_year |
+----------------------------------+---------------+
| A Hologram for the King: A Novel |          2012 |
| The Circle                       |          2013 |
| Just Kids                        |          2010 |
| Oblivion: Stories                |          2004 |
| Consider the Lobster             |          2005 |
| 10% Happier                      |          2014 |
+----------------------------------+---------------+
6 rows in set (0.01 sec)

mysql> SELECT
    ->   title,
    ->   released_year
    -> FROM books
    -> WHERE released_year BETWEEN 2004 AND 2015;
+----------------------------------+---------------+
| title                            | released_year |
+----------------------------------+---------------+
| A Hologram for the King: A Novel |          2012 |
| The Circle                       |          2013 |
| Just Kids                        |          2010 |
| Oblivion: Stories                |          2004 |
| Consider the Lobster             |          2005 |
| 10% Happier                      |          2014 |
+----------------------------------+---------------+
6 rows in set (0.00 sec)

mysql> SELECT
    ->   title,
    ->   released_year
    -> FROM books
    -> WHERE released_year NOT BETWEEN 2004 AND 2015;
+-----------------------------------------------------+---------------+
| title                                               | released_year |
+-----------------------------------------------------+---------------+
| The Namesake                                        |          2003 |
| Norse Mythology                                     |          2016 |
| American Gods                                       |          2001 |
| Interpreter of Maladies                             |          1996 |
| The Amazing Adventures of Kavalier & Clay           |          2000 |
| A Heartbreaking Work of Staggering Genius           |          2001 |
| Coraline                                            |          2003 |
| What We Talk About When We Talk About Love: Stories |          1981 |
| Where I'm Calling From: Selected Stories            |          1989 |
| White Noise                                         |          1985 |
| Cannery Row                                         |          1945 |
| fake_book                                           |          2001 |
| Lincoln In The Bardo                                |          2017 |
+-----------------------------------------------------+---------------+
13 rows in set (0.00 sec)

mysql> SELECT CAST('2017-05-02' AS DATETIME);
+--------------------------------+
| CAST('2017-05-02' AS DATETIME) |
+--------------------------------+
| 2017-05-02 00:00:00            |
+--------------------------------+
1 row in set (0.03 sec)
```
## IN and NOT IN
```
mysql> SELECT
    ->     title,
    ->     author_lname
    -> FROM books
    -> WHERE author_lname='Carver' OR
    ->       author_lname='Lahiri' OR
    ->       author_lname='Smith';
+-----------------------------------------------------+--------------+
| title                                               | author_lname |
+-----------------------------------------------------+--------------+
| The Namesake                                        | Lahiri       |
| Interpreter of Maladies                             | Lahiri       |
| Just Kids                                           | Smith        |
| What We Talk About When We Talk About Love: Stories | Carver       |
| Where I'm Calling From: Selected Stories            | Carver       |
+-----------------------------------------------------+--------------+
5 rows in set (0.02 sec)

mysql> SELECT title, author_lname FROM books
    -> WHERE author_lname IN ('Carver', 'Lahiri', 'Smith');
+-----------------------------------------------------+--------------+
| title                                               | author_lname |
+-----------------------------------------------------+--------------+
| The Namesake                                        | Lahiri       |
| Interpreter of Maladies                             | Lahiri       |
| Just Kids                                           | Smith        |
| What We Talk About When We Talk About Love: Stories | Carver       |
| Where I'm Calling From: Selected Stories            | Carver       |
+-----------------------------------------------------+--------------+
5 rows in set (0.00 sec)

mysql> SELECT title, released_year FROM books
    -> WHERE released_year IN (2017, 1985);
+----------------------+---------------+
| title                | released_year |
+----------------------+---------------+
| White Noise          |          1985 |
| Lincoln In The Bardo |          2017 |
+----------------------+---------------+
2 rows in set (0.00 sec)

mysql> SELECT title, released_year FROM books
    -> WHERE released_year != 2000 AND
    ->       released_year != 2002 AND
    ->       released_year != 2004 AND
    ->       released_year != 2006 AND
    ->       released_year != 2008 AND
    ->       released_year != 2010 AND
    ->       released_year != 2012 AND
    ->       released_year != 2014 AND
    ->       released_year != 2016;
+-----------------------------------------------------+---------------+
| title                                               | released_year |
+-----------------------------------------------------+---------------+
| The Namesake                                        |          2003 |
| American Gods                                       |          2001 |
| Interpreter of Maladies                             |          1996 |
| The Circle                                          |          2013 |
| A Heartbreaking Work of Staggering Genius           |          2001 |
| Coraline                                            |          2003 |
| What We Talk About When We Talk About Love: Stories |          1981 |
| Where I'm Calling From: Selected Stories            |          1989 |
| White Noise                                         |          1985 |
| Cannery Row                                         |          1945 |
| Consider the Lobster                                |          2005 |
| fake_book                                           |          2001 |
| Lincoln In The Bardo                                |          2017 |
+-----------------------------------------------------+---------------+

mysql> SELECT title, released_year FROM books
    -> WHERE released_year NOT IN
    -> (2000,2002,2004,2006,2008,2010,2012,2014,2016);
+-----------------------------------------------------+---------------+
| title                                               | released_year |
+-----------------------------------------------------+---------------+
| The Namesake                                        |          2003 |
| American Gods                                       |          2001 |
| Interpreter of Maladies                             |          1996 |
| The Circle                                          |          2013 |
| A Heartbreaking Work of Staggering Genius           |          2001 |
| Coraline                                            |          2003 |
| What We Talk About When We Talk About Love: Stories |          1981 |
| Where I'm Calling From: Selected Stories            |          1989 |
| White Noise                                         |          1985 |
| Cannery Row                                         |          1945 |
| Consider the Lobster                                |          2005 |
| fake_book                                           |          2001 |
| Lincoln In The Bardo                                |          2017 |
+-----------------------------------------------------+---------------+
13 rows in set (0.00 sec)

mysql> SELECT title, released_year FROM books
    -> WHERE released_year >= 2000 AND
    -> released_year % 2 != 0 ORDER BY released_year;
+-------------------------------------------+---------------+
| title                                     | released_year |
+-------------------------------------------+---------------+
| American Gods                             |          2001 |
| A Heartbreaking Work of Staggering Genius |          2001 |
| fake_book                                 |          2001 |
| The Namesake                              |          2003 |
| Coraline                                  |          2003 |
| Consider the Lobster                      |          2005 |
| The Circle                                |          2013 |
| Lincoln In The Bardo                      |          2017 |
+-------------------------------------------+---------------+
8 rows in set (0.01 sec)
```
## Case Statements
```
mysql> SELECT
    ->   title,
    ->   released_year,
    ->   CASE
    ->     WHEN released_year >= 2000 THEN 'Modern Lit'
    ->     ELSE '20th Century Lit'
    ->   END AS GENRE
    -> FROM books;
+-----------------------------------------------------+---------------+------------------+
| title                                               | released_year | GENRE            |
+-----------------------------------------------------+---------------+------------------+
| The Namesake                                        |          2003 | Modern Lit       |
| Norse Mythology                                     |          2016 | Modern Lit       |
| American Gods                                       |          2001 | Modern Lit       |
| Interpreter of Maladies                             |          1996 | 20th Century Lit |
| A Hologram for the King: A Novel                    |          2012 | Modern Lit       |
| The Circle                                          |          2013 | Modern Lit       |
| The Amazing Adventures of Kavalier & Clay           |          2000 | Modern Lit       |
| Just Kids                                           |          2010 | Modern Lit       |
| A Heartbreaking Work of Staggering Genius           |          2001 | Modern Lit       |
| Coraline                                            |          2003 | Modern Lit       |
| What We Talk About When We Talk About Love: Stories |          1981 | 20th Century Lit |
| Where I'm Calling From: Selected Stories            |          1989 | 20th Century Lit |
| White Noise                                         |          1985 | 20th Century Lit |
| Cannery Row                                         |          1945 | 20th Century Lit |
| Oblivion: Stories                                   |          2004 | Modern Lit       |
| Consider the Lobster                                |          2005 | Modern Lit       |
| 10% Happier                                         |          2014 | Modern Lit       |
| fake_book                                           |          2001 | Modern Lit       |
| Lincoln In The Bardo                                |          2017 | Modern Lit       |
+-----------------------------------------------------+---------------+------------------+
19 rows in set (0.01 sec)

mysql> SELECT title, stock_quantity,
    ->     CASE
    ->         WHEN stock_quantity BETWEEN 0 AND 50 THEN '*'
    ->         WHEN stock_quantity BETWEEN 51 AND 100 THEN '**'
    ->         ELSE '***'
    ->     END AS STOCK
    -> FROM books;
+-----------------------------------------------------+----------------+-------+
| title                                               | stock_quantity | STOCK |
+-----------------------------------------------------+----------------+-------+
| The Namesake                                        |             32 | *     |
| Norse Mythology                                     |             43 | *     |
| American Gods                                       |             12 | *     |
| Interpreter of Maladies                             |             97 | **    |
| A Hologram for the King: A Novel                    |            154 | ***   |
| The Circle                                          |             26 | *     |
| The Amazing Adventures of Kavalier & Clay           |             68 | **    |
| Just Kids                                           |             55 | **    |
| A Heartbreaking Work of Staggering Genius           |            104 | ***   |
| Coraline                                            |            100 | **    |
| What We Talk About When We Talk About Love: Stories |             23 | *     |
| Where I'm Calling From: Selected Stories            |             12 | *     |
| White Noise                                         |             49 | *     |
| Cannery Row                                         |             95 | **    |
| Oblivion: Stories                                   |            172 | ***   |
| Consider the Lobster                                |             92 | **    |
| 10% Happier                                         |             29 | *     |
| fake_book                                           |            287 | ***   |
| Lincoln In The Bardo                                |           1000 | ***   |
+-----------------------------------------------------+----------------+-------+
19 rows in set (0.00 sec)

mysql> SELECT title, stock_quantity,
    ->     CASE
    ->         WHEN stock_quantity <= 50 THEN '*'
    ->         WHEN stock_quantity <= 100 THEN '**'
    ->         ELSE '***'
    ->     END AS STOCK
    -> FROM books;
+-----------------------------------------------------+----------------+-------+
| title                                               | stock_quantity | STOCK |
+-----------------------------------------------------+----------------+-------+
| The Namesake                                        |             32 | *     |
| Norse Mythology                                     |             43 | *     |
| American Gods                                       |             12 | *     |
| Interpreter of Maladies                             |             97 | **    |
| A Hologram for the King: A Novel                    |            154 | ***   |
| The Circle                                          |             26 | *     |
| The Amazing Adventures of Kavalier & Clay           |             68 | **    |
| Just Kids                                           |             55 | **    |
| A Heartbreaking Work of Staggering Genius           |            104 | ***   |
| Coraline                                            |            100 | **    |
| What We Talk About When We Talk About Love: Stories |             23 | *     |
| Where I'm Calling From: Selected Stories            |             12 | *     |
| White Noise                                         |             49 | *     |
| Cannery Row                                         |             95 | **    |
| Oblivion: Stories                                   |            172 | ***   |
| Consider the Lobster                                |             92 | **    |
| 10% Happier                                         |             29 | *     |
| fake_book                                           |            287 | ***   |
| Lincoln In The Bardo                                |           1000 | ***   |
+-----------------------------------------------------+----------------+-------+
19 rows in set (0.00 sec)
```
## Logical Operators Challenge
```
mysql> SELECT
    ->     title,
    ->     author_lname
    -> FROM books
    -> WHERE
    ->     author_lname LIKE 'C%' OR
    ->     author_lname LIKE 'S%';
+-----------------------------------------------------+--------------+
| title                                               | author_lname |
+-----------------------------------------------------+--------------+
| The Amazing Adventures of Kavalier & Clay           | Chabon       |
| Just Kids                                           | Smith        |
| What We Talk About When We Talk About Love: Stories | Carver       |
| Where I'm Calling From: Selected Stories            | Carver       |
| Cannery Row                                         | Steinbeck    |
| Lincoln In The Bardo                                | Saunders     |
+-----------------------------------------------------+--------------+
6 rows in set (0.04 sec)

mysql> SELECT
    ->     title,
    ->     author_lname
    -> FROM books
    -> WHERE
    ->     SUBSTR(author_lname,1,1) = 'C' OR
    ->     SUBSTR(author_lname,1,1) = 'S';
+-----------------------------------------------------+--------------+
| title                                               | author_lname |
+-----------------------------------------------------+--------------+
| The Amazing Adventures of Kavalier & Clay           | Chabon       |
| Just Kids                                           | Smith        |
| What We Talk About When We Talk About Love: Stories | Carver       |
| Where I'm Calling From: Selected Stories            | Carver       |
| Cannery Row                                         | Steinbeck    |
| Lincoln In The Bardo                                | Saunders     |
+-----------------------------------------------------+--------------+
6 rows in set (0.01 sec)

mysql> SELECT title, author_lname FROM books
    -> WHERE SUBSTR(author_lname,1,1) IN ('C', 'S');
+-----------------------------------------------------+--------------+
| title                                               | author_lname |
+-----------------------------------------------------+--------------+
| The Amazing Adventures of Kavalier & Clay           | Chabon       |
| Just Kids                                           | Smith        |
| What We Talk About When We Talk About Love: Stories | Carver       |
| Where I'm Calling From: Selected Stories            | Carver       |
| Cannery Row                                         | Steinbeck    |
| Lincoln In The Bardo                                | Saunders     |
+-----------------------------------------------------+--------------+
6 rows in set (0.00 sec)

mysql> SELECT
    ->     title,
    ->     author_lname,
    ->     CASE
    ->         WHEN title LIKE '%stories%' THEN 'Short Stories'
    ->         WHEN title = 'Just Kids' OR title = 'A Heartbreaking Work of Staggering Genius' THEN 'Memoir'

    ->         ELSE 'Novel'
    ->     END AS TYPE
    -> FROM books;
+-----------------------------------------------------+----------------+---------------+
| title                                               | author_lname   | TYPE          |
+-----------------------------------------------------+----------------+---------------+
| The Namesake                                        | Lahiri         | Novel         |
| Norse Mythology                                     | Gaiman         | Novel         |
| American Gods                                       | Gaiman         | Novel         |
| Interpreter of Maladies                             | Lahiri         | Novel         |
| A Hologram for the King: A Novel                    | Eggers         | Novel         |
| The Circle                                          | Eggers         | Novel         |
| The Amazing Adventures of Kavalier & Clay           | Chabon         | Novel         |
| Just Kids                                           | Smith          | Memoir        |
| A Heartbreaking Work of Staggering Genius           | Eggers         | Memoir        |
| Coraline                                            | Gaiman         | Novel         |
| What We Talk About When We Talk About Love: Stories | Carver         | Short Stories |
| Where I'm Calling From: Selected Stories            | Carver         | Short Stories |
| White Noise                                         | DeLillo        | Novel         |
| Cannery Row                                         | Steinbeck      | Novel         |
| Oblivion: Stories                                   | Foster Wallace | Short Stories |
| Consider the Lobster                                | Foster Wallace | Novel         |
| 10% Happier                                         | Harris         | Novel         |
| fake_book                                           | Harris         | Novel         |
| Lincoln In The Bardo                                | Saunders       | Novel         |
+-----------------------------------------------------+----------------+---------------+
19 rows in set (0.01 sec)

mysql> SELECT author_fname, author_lname,
    ->     CASE
    ->         WHEN COUNT(*) = 1 THEN '1 book'
    ->         ELSE CONCAT(COUNT(*), ' books')
    ->     END AS COUNT
    -> FROM books
    -> GROUP BY author_lname, author_fname;
+--------------+----------------+---------+
| author_fname | author_lname   | COUNT   |
+--------------+----------------+---------+
| Raymond      | Carver         | 2 books |
| Michael      | Chabon         | 1 book  |
| Don          | DeLillo        | 1 book  |
| Dave         | Eggers         | 3 books |
| David        | Foster Wallace | 2 books |
| Neil         | Gaiman         | 3 books |
| Dan          | Harris         | 1 book  |
| Freida       | Harris         | 1 book  |
| Jhumpa       | Lahiri         | 2 books |
| George       | Saunders       | 1 book  |
| Patti        | Smith          | 1 book  |
| John         | Steinbeck      | 1 book  |
+--------------+----------------+---------+
12 rows in set (0.06 sec)
```
