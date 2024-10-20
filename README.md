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
 Scheme name — “LibraryManagement”

SQL queries:

``` mysql 
    CREATE SCHEMA LibraryManagement;
```

Result:

![](/1.DB_structure/1.a.Create_schema.png)

## Task1b
 "authors" table:

 author_id (INT, auto-increment PRIMARY KEY)
 author_name (VARCHAR)

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
 Table "genres":

 genre_id (INT, auto-increment PRIMARY KEY)
 genre_name (VARCHAR)

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
 Table "books":

 book_id (INT, auto-increment PRIMARY KEY)
 title (VARCHAR)
 publication_year (YEAR)
 author_id (INT, FOREIGN KEY relation to "Authors")
 genre_id (INT, FOREIGN KEY relation to "Genres")

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
Table "users":

 user_id (INT, auto-increment PRIMARY KEY)
 username (VARCHAR)
 email (VARCHAR)

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
 Table "borrowed_books":

 borrow_id (INT, auto-increment PRIMARY KEY)
 book_id (INT, FOREIGN KEY relation to "Books")
 user_id (INT, FOREIGN KEY relation to "Users")
 borrow_date (DATE)
 return_date (DATE)

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



