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
