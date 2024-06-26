Make sure you download the starter code and run the following:

```sh
  psql < movies.sql
  psql movies_db
```

In markdown, you can place a code block inside of three backticks (```) followed by the syntax highlighting you want, for example

\```sql

SELECT \* FROM users;

\```

Using the `movies_db` database, write the correct SQL queries for each of these tasks:

1.  The title of every movie.
    `SELECT title FROM movies;`

2.  All information on the G-rated movies.
    `SELECT * FROM movies WHERE rating = 'G'`

3.  The title and release year of every movie, ordered with the
    oldest movie first.
    `SELECT title, release_year FROM movies ORDER BY release_year`;
4.  All information on the 5 longest movies.
    `SELECT * FROM movies ORDER BY runtime DESC LIMIT 5;`

5.  A query that returns the columns of `rating` and `total`, tabulating the
    total number of G, PG, PG-13, and R-rated movies.

`SELECT rating, COUNT(rating) as total FROM movies GROUP BY rating;`

6.  A table with columns of `release_year` and `average_runtime`,
    tabulating the average runtime by year for every movie in the database. The data should be in reverse chronological order (i.e. the most recent year should be first).

    `SELECT release_year, AVG(runtime) FROM movies GROUP BY release_year ORDER BY release_year DESC;`

7.  The movie title and studio name for every movie in the
    database.

    `SELECT title AS movie_title, name AS studio_name FROM movies JOIN studios on movies.studio_id=studios.id;`

8.  The star first name, star last name, and movie title for every
    matching movie and star pair in the database.
    `SELECT first_name, last_name, title FROM roles JOIN stars ON roles.star_id = stars.id JOIN movies ON roles.movie_id =movies.id;`.

9.  The first and last names of every star who has been in a G-rated movie. The first and last name should appear only once for each star, even if they are in several G-rated movies. _IMPORTANT NOTE_: it's possible that there can be two _different_ actors with the same name, so make sure your solution accounts for that.
    `SELECT first_name, last_name FROM roles JOIN stars ON roles.star_id = stars.id JOIN movies ON roles.movie_id = movies.id WHERE rating = 'G' GROUP BY stars.id;`

10. The first and last names of every star along with the number
    of movies they have been in, in descending order by the number of movies. (Similar to #9, make sure
    that two different actors with the same name are considered separately).

`SELECT first_name, last_name, COUNT(star_id) as movie_count FROM roles JOIN stars ON roles.star_id = stars.id JOIN movies ON roles.movie_id = movies.id GROUP BY first_name, last_name ORDER BY movie_count DESC;`

### The rest of these are bonuses

11. The title of every movie along with the number of stars in
    that movie, in descending order by the number of stars.

    `SELECT title AS movie_name, COUNT(stars) AS num_stars FROM roles JOIN movies ON roles.movie_id = movies.id JOIN stars ON roles.star_id=stars.id GROUP BY title ORDER BY COUNT(stars) DESC;`

12. The first name, last name, and average runtime of the five
    stars whose movies have the longest average.

    `SELECT first_name, last_name, AVG(runtime) AS average_runtime FROM roles JOIN stars ON roles.star_id = stars.id JOIN movies ON roles.movie_id = movies.id GROUP BY first_name, last_name ORDER BY AVG(runtime) DESC LIMIT 5;`

13. The first name, last name, and average runtime of the five
    stars whose movies have the longest average, among stars who have more than one movie in the database.

    `SELECT first_name, last_name, AVG(runtime) AS average_runtime FROM roles JOIN stars ON roles.star_id = stars.id JOIN movies ON roles.movie_id = movies.id GROUP BY first_name, last_name HAVING COUNT(title) > 1 ORDER BY average_runtime DESC LIMIT 5;`

14. The titles of all movies that don't feature any stars in our
    database.
    `SELECT title FROM movies LEFT JOIN roles ON movies.id = roles.movie_id WHERE roles.star_id IS NULL;`

15. The first and last names of all stars that don't appear in any movies in our database.

16. The first names, last names, and titles corresponding to every
    role in the database, along with every movie title that doesn't have a star, and the first and last names of every star not in a movie.
