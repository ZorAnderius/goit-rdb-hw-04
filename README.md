# DML and DDL commands (HW3)

## Content

- [Task1](#Task1)
- [Task1a](#Task1a)
- [Task1b](#Task1b)
- [Task1c](#Task1c)
- [Task1d](#Task1d)
- [Task1e](#Task1e)
- [Task1f](#Task1f)
- [Task2](#Task2)
- [Task3](#Task3)
- [Task4](#Task4)
- [Task4-1](#Task4-1)
- [Task4-2](#Task4-2)
- [Task4-3](#Task4-3)
- [Task4-4](#Task4-4)
- [Task4-5](#Task4-5)
- [Task4-6](#Task4-6)
- [Task4-7](#Task4-7)

## Task1

Create a database to manage the book library according to the structure given below. Use DDL commands to create the necessary tables and their relationships.



Database structure

## Task1a
 Scheme name — *“LibraryManagement”*

SQL queries:

``` mysql 
    CREATE SCHEMA LibraryManagement;
```

Result:

![](/1.DB_structure/1.a.Create_schema.png)

## Task1b
 Create "authors" table:

 - *author_id (INT, auto-increment PRIMARY KEY)*
 - *author_name (VARCHAR)*

 SQL queries:

``` mysql 
    use librarymanagment;

    CREATE TABLE authors (
        author_id INT AUTO_INCREMENT PRIMARY KEY,
        author_name VARCHAR(60)
    );
```

Result:

![](/1.DB_structure/1.b.Authors%20_table.png)

## Task1c
 Create table "genres":

  - *genre_id (INT, auto-increment PRIMARY KEY)*
  - *genre_name (VARCHAR)*

 SQL queries:

``` mysql 
    use librarymanagment;

    CREATE TABLE genres (
        genre_id INT AUTO_INCREMENT PRIMARY KEY,
        genre_name VARCHAR(60)
    );
```

Result:

![](/1.DB_structure/1.c.Genres%20_table.png)

## Task1d
 Create table "books":

 - *book_id (INT, auto-increment PRIMARY KEY)*
 - *title (VARCHAR)*
 - *publication_year (YEAR)*
 - *author_id (INT, FOREIGN KEY relation to "Authors")*
 - *genre_id (INT, FOREIGN KEY relation to "Genres")*

 SQL queries:

``` mysql 
    use librarymanagment;

    CREATE TABLE books (
        book_id INT AUTO_INCREMENT PRIMARY KEY,
        title VARCHAR(60),
        publication_year YEAR,
        author_id INT,
        genre_id INT,
        FOREIGN KEY (author_id) REFERENCES authors(author_id),
        FOREIGN KEY (genre_id) REFERENCES genres(genre_id)
    );
```

Result:

![](/1.DB_structure/1.d.Books_table.png)

## Task1e 
Create table "users":

 - *user_id (INT, auto-increment PRIMARY KEY)*
 - *username (VARCHAR)*
 - *email (VARCHAR)*

 SQL queries:

``` mysql 
    use librarymanagment;

    CREATE TABLE users (
        user_id INT AUTO_INCREMENT PRIMARY KEY,
        username VARCHAR(60),
        email VARCHAR(60)
    );
```

Result:

![](/1.DB_structure/1.e.Users_table.png)

## Task1f
 Create table "borrowed_books":

 - *borrow_id (INT, auto-increment PRIMARY KEY)*
 - *book_id (INT, FOREIGN KEY relation to "Books")*
 - *user_id (INT, FOREIGN KEY relation to "Users")*
 - *borrow_date (DATE)*
 - *return_date (DATE)*

 SQL queries:

``` mysql 
    use librarymanagment;

    CREATE TABLE borrowed_books (
        borrow_id INT AUTO_INCREMENT PRIMARY KEY,
        borrow_date DATE,
        return_date DATE,
        book_id INT,
        user_id INT,
        FOREIGN KEY (book_id) REFERENCES books(book_id),
        FOREIGN KEY (user_id) REFERENCES users(user_id)
    );
```

Result:

![](/1.DB_structure/1.f.Borrowed_books_table.png)



## Task2
 Fill in the tables with simple fictitious test data. One or two rows in each table are enough.

 - *author table:*

 
 SQL queries:


``` mysql 
    use librarymanagment;

    INSERT INTO authors (author_name)
    VALUES 
    ('George Orwell'),
    ('Colleen Hoover'),
    ('Ernest Hemingway'),
    ('J.K. Rowling'),
    ('F. Scott Fitzgerald');
```

Result:

![](/2.Insert_data/2.a.Authors_table.png)


 - *genres table:*

 SQL queries:


``` mysql 
    use librarymanagment;

    INSERT INTO genres (genre_name)
    VALUES 
    ('dystopia'),
    ('political satire'),
    ('memoir'),
    ('romance'),
    ('fiction'),
    ('drama'),
    ('fantasy'),
    ('tragedy');
```

Result:

![](/2.Insert_data/2.b.Genres_table.png)


 - *books table:*

  SQL queries:


``` mysql 
    use librarymanagment;

    INSERT INTO books (title, publication_year, author_id, genre_id)
    VALUES 
    ('1984', 1949, 1, 1),
    ('Animal Farm', 1945, 1, 2),
    ('Homage to Catalonia', 1938, 1, 3),
    ('It Ends with Us', 2016, 2, 4),
    ('Verity', 2018, 2, 4),
    ('Reminders of Him', 2022, 2, 4),
    ('The Old Man and the Sea', 1952, 3, 5),
    ('For Whom the Bell Tolls', 1940, 3, 5),
    ('A Farewell to Arms', 1929, 3, 5),
    ('Harry Potter and the Philosopher\'s Stone',  1997, 4, 7),
    ('Harry Potter and the Chamber of Secrets', 1998, 4, 7),
    ('Harry Potter and the Prisoner of Azkaban', 1999, 4, 7),
    ('The Great Gatsby',  1925, 5, 8),
    ('Tender is the Night', 1934, 5, 8),
    ('This Side of Paradise', 1920, 5, 5);
```

Result:

![](/2.Insert_data/2.c.Books_table.png)


 - *users table:*

  SQL queries:


``` mysql 
    use librarymanagment;

    INSERT INTO users (username, email)
    VALUES 
    ('John Snow', 'snow.jogn@gmaol.com'),
    ('Anna Porretti', 'poretti@gmai.com'),
    ('John Doe', 'john.doe@gmail.com'),
    ('Ivan Dolphy', 'dolphy@gmai.com'),
    ('Nory Vertega', 'vertega@gmai.com');
```

Result:

![](/2.Insert_data/2.d.User_table.png)


 - *Borrowed_books table:*

  SQL queries:


``` mysql 
    use librarymanagment;

    INSERT INTO borrowed_books (borrow_date, return_date, book_id, user_id)
    VALUES 
    ('2024-10-16', '2024-10-30', 16, 2),
    ('2024-09-23', '2024-10-28', 17, 1),
    ('2024-10-12', '2024-12-02', 18, 5),
    ('2024-10-16', '2024-10-29', 19, 4),
    ('2024-10-15', '2024-10-30', 20, 3),
    ('2024-10-16', '2024-10-30', 21, 2),
    ('2024-09-23', '2024-10-28', 22, 1),
    ('2024-10-12', '2024-12-02', 23, 1),
    ('2024-10-16', '2024-10-29', 24, 4),
    ('2024-10-15', '2024-10-30', 25, 1),
    ('2024-10-16', '2024-10-30', 26, 2),
    ('2024-09-23', '2024-10-28', 27, 1),
    ('2024-10-12', '2024-12-02', 28, 5),
    ('2024-10-16', '2024-10-29', 29, 5),
    ('2024-10-15', '2024-10-30', 30, 3);
```

Result:

![](/2.Insert_data/2.e.Borrowed_books_table.png)


## Task3
Go to the database that you worked with in Topic 3. Write a query using the FROM and INNER JOIN statements that joins all the data tables that we loaded from the files: order_details, orders, customers, products, categories, employees, shippers, suppliers. To do this, you need to find shared keys.

Check the correct execution of the request.

SQL queries:

``` mysql 
    use hw2;

    SELECT order_id AS 'Order number', 
        o.date AS 'Order date',
        p.name AS 'Product name',
        categ.name AS 'Category',
        quantity,
        (quantity * p.price) AS 'Total price',
        c.name AS 'Customer name',
        c.contact AS 'Customer contact',
        c.address AS 'Customer address',
        CONCAT(e.first_name, ' ', e.last_name) AS 'Employee full name',
        e.birthdate AS 'Employee birthday',
        s.name AS 'Supplier name',
        s.phone AS 'Supplier phone',
        ship.name AS 'Shipper name',
        ship.phone AS 'Shipper phone'
    FROM order_details
    INNER JOIN  products AS p ON order_details.product_id = p.id
    INNER JOIN categories AS categ ON p.category_id = categ.id
    INNER JOIN suppliers AS s ON p.supplier_id = s.id
    INNER JOIN orders AS o ON order_details.order_id = o.id
    INNER JOIN customers AS c ON o.customer_id = c.id
    INNER JOIN employees AS e ON o.employee_id = e.employee_id
    INNER JOIN shippers AS ship ON o.shipper_id = ship.id;
```

Also, as result of queries you can check follow file - ![Result of join](3.result_tabel.csv) 


Result:

![](/3.Inner_join/3.Inner_join.png)
