### Conceptual Exercise

Answer the following questions below:

- What is PostgreSQL?

Postgres is a RDBMS. This is one such RDBMS that allows for creating, updating, manipulating, deleting, etc relations in databases through SQL queries and syntax.

- What is the difference between SQL and PostgreSQL?

SQL is a specific querying language, whereas PostgresSQL is the RDBMS that uses this language to manage databases.

- In `psql`, how do you connect to a database?

You type \c and then the name of the database and then a semicolon.

- What is the difference between `HAVING` and `WHERE`?
  WHERE is used to modify SELECT statements or rows of data. It is used after FROM. The HAVING keyword is similar except, but it is used after GROUP BY or after the rows have been grouped based off some aggregator.

- What is the difference between an `INNER` and `OUTER` join?
  For inner joins we show the rows in two tables that share the same information only. If the rows fomr each table do not match one another, it is not included in the join.

There are different types of outer joins, but basically, it can show the results of all the rows from one table and the results from the other table that match some of those results. It does not include the rows from the other table that do not match the first table.

- What is the difference between a `LEFT OUTER` and `RIGHT OUTER` join?

In a left outer join all rows from the left table are included in the join and just the matching rows from the right table. The right outer join is just the opposite—all of the rows from the right table are included and only the matching rows of the left table.

- What is an ORM? What do they do?

It maps objects in a specific programming language (like Python) to queries in a database language like SQL. This allows us to interact with databases without using specific database syntax.

- What are some differences between making HTTP requests using AJAX
  and from the server side using a library like `requests`?

  http requests using ajax are made from the client side. The browser makes a request to an external API ands gets data back. This can be faster than using a library like requests. Although, some websites may enforce a same origin policy which prevents client side requests. Also, if an API is password protected it is best to make server side requests

- What is CSRF? What is the purpose of the CSRF token?

CSRF stands for cross site request forgery, a CSRF token prevents people from sending post request info to the server that does not come from the intended form. WTForms generates this token automatically and it is used in a hidden field.

- What is the purpose of `form.hidden_tag()`?

It creates a hidden field in a form for the CSRF token in WtForms.
