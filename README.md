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


## Task4

Follow the prompts listed below.

## Task4-1

Determine how many rows you got (using the COUNT operator).

SQL queries:

``` mysql 
    use hw2;

    SELECT COUNT(order_id) AS 'Total orders'
    FROM order_details
    INNER JOIN  products AS p ON order_details.product_id = p.id
    INNER JOIN categories AS categ ON p.category_id = categ.id
    INNER JOIN suppliers AS s ON p.supplier_id = s.id
    INNER JOIN orders AS o ON order_details.order_id = o.id
    INNER JOIN customers AS c ON o.customer_id = c.id
    INNER JOIN employees AS e ON o.employee_id = e.employee_id
    INNER JOIN shippers AS ship ON o.shipper_id = ship.id;
```

Result:

![](/4.Answers//4.1.Count.png)


## Task4-2

Change several INNER statements to LEFT or RIGHT. Determine what happens to the number of rows. Why?

For a better comparison, consider several options for sampling using JOIN, namely:
- *only LEFT JOIN*
- *only RIGHT JOIN*
- *LEFT and RIGHT JOIN (change by one)*
- *several tables through RIGHT JOIN, and others through LEFT*


*LEFT JOIN*


SQL queries:

``` mysql 
    use hw2;

    SELECT COUNT(order_id) AS 'Total orders'
    FROM order_details
    LEFT JOIN  products AS p ON order_details.product_id = p.id
    LEFT JOIN categories AS categ ON p.category_id = categ.id
    LEFT JOIN suppliers AS s ON p.supplier_id = s.id
    LEFT JOIN orders AS o ON order_details.order_id = o.id
    LEFT JOIN customers AS c ON o.customer_id = c.id
    LEFT JOIN employees AS e ON o.employee_id = e.employee_id
    LEFT JOIN shippers AS ship ON o.shipper_id = ship.id;
```

Result:

![](/4.Answers//4.2.1LEFT_JOIN.png)


*RIGHT JOIN*


SQL queries:

``` mysql 
    use hw2;

    SELECT COUNT(order_id) AS 'Total orders'
    FROM order_details
    RIGHT JOIN  products AS p ON order_details.product_id = p.id
    RIGHT JOIN categories AS categ ON p.category_id = categ.id
    RIGHT JOIN suppliers AS s ON p.supplier_id = s.id
    RIGHT JOIN orders AS o ON order_details.order_id = o.id
    RIGHT JOIN customers AS c ON o.customer_id = c.id
    RIGHT JOIN employees AS e ON o.employee_id = e.employee_id
    RIGHT JOIN shippers AS ship ON o.shipper_id = ship.id;
```

Result:

![](/4.Answers//4.2.2.RIGHT_JOIN.png)

*RIGHT/LEFT JOIN (change by one)*


SQL queries:

``` mysql 
    use hw2;

    SELECT COUNT(order_id) AS 'Total orders'
    FROM order_details
    RIGHT JOIN  products AS p ON order_details.product_id = p.id
    LEFT JOIN categories AS categ ON p.category_id = categ.id
    RIGHT JOIN suppliers AS s ON p.supplier_id = s.id
    LEFT JOIN orders AS o ON order_details.order_id = o.id
    RIGHT JOIN customers AS c ON o.customer_id = c.id
    LEFT JOIN employees AS e ON o.employee_id = e.employee_id
    RIGHT JOIN shippers AS ship ON o.shipper_id = ship.id;
```

Result:

![](/4.Answers//4.2.3.RIGHT&LEFT_JOIN(ODD&EVEN).png)

*RIGHT/LEFT JOIN*


SQL queries:

``` mysql 
    use hw2;

    SELECT COUNT(order_id) AS 'Total orders'
    FROM order_details
    RIGHT JOIN  products AS p ON order_details.product_id = p.id
    RIGHT JOIN categories AS categ ON p.category_id = categ.id
    RIGHT JOIN suppliers AS s ON p.supplier_id = s.id
    RIGHT JOIN orders AS o ON order_details.order_id = o.id
    LEFT JOIN customers AS c ON o.customer_id = c.id
    LEFT JOIN employees AS e ON o.employee_id = e.employee_id
    LEFT JOIN shippers AS ship ON o.shipper_id = ship.id;
```

Result:

![](/4.Answers//4.2.4.RIGHTandLEFT_JOIN.png)


Main result: 
<div>
  <button onclick="openTab(event, 'ukrainian')" style="padding:10px; cursor: pointer;">Українська</button>
  <button onclick="openTab(event, 'english')" style="padding:10px; cursor: pointer;">English</button>
</div>

<div id="ukrainian" class="tab-content" style="display:block;">
  
  ## УКР

 В результаті проведеного дослідження видно, що вибірка загальної кількості ордерів через LEFT, RIGHT або INNER JOIN нічим не відрізняються. Це можливо через сильну кореляцію даних. Однак в деяких випадках помітно значне зростання часу відповіді. Наприклад, якщо виберемо тільки LEFT JOIN, то швидкість виконання становить від 0 до 0.016 с. В той час як при вибірці даних з RIGHT JOIN час виконання становить приблизно 0.7 с (здійснено декілька запитів). Якщо ж задати один RIGHT та один LEFT JOIN, і подальше їх чергування за таким патерном, то час виникає помилка  (що може бути причиною певних конфліктів). Якщо ж задати вибірку з перших декількох таблиць за RIGHT JOIN, а решту, за LEFT JOIN, то час запиту становить приблизно як і для варіанту з тільки RIGHT JOIN, а саме, 0.65 с.
 Варто зазначити, що час тривалості запиту з INNER JOINстановить в середньому 0.078 с. 
 Виходячи з цього, можна зробити висновок, що для даного сценарію найкращим варіантом являється вибірка з допомогою LEFT JOIN та INNER JOIN. Всі ж запити з використанням RIGHT JOIN займали набагато більше часу, а в деяких випадках, взагалі призводить до помилки. Можливо проблема з RIGHT JOIN є в тому, що в більшості запити виконуються через LEFT JOIN і як наслідок оптимізація запитів з RIGHT JOIN є не дотатньою. Крім того, на практиці здебільшого використовують LEFT JOIN. А комбінацію LEFT та RIGHT JOIN взагалі не потрібно використовувати  через їх можливий конфліктну та взаємопротилежну сутність. Тому для вибірки даних найоптимальнішим варіантом є LEFT JOIN.

</div>
<div id="english" class="tab-content" style="display:none;">
  
  ## English Version
As a result of the conducted research, it can be seen that the sampling of the total number of orders through LEFT, RIGHT or INNER JOIN does not differ. This is possible due to the strong correlation of the data. However, in some cases, a significant increase in response time is noticeable. For example, if we choose only LEFT JOIN, the execution speed is from 0 to 0.016 s. While when retrieving data from RIGHT JOIN, the execution time is approximately 0.7 s (several requests are made). If you specify one RIGHT and one LEFT JOIN, and their subsequent alternation according to this pattern, then an error occurs (which may be the cause of certain conflicts). If you specify a selection from the first few tables by RIGHT JOIN, and the rest by LEFT JOIN, then the query time is approximately the same as for the option with only RIGHT JOIN, namely, 0.65 s.
 It is worth noting that the INNER JOIN request takes an average of 0.078 seconds.
 Based on this, we can conclude that for this scenario, the best option is the LEFT JOIN and INNER JOIN selection. All requests using RIGHT JOIN took much more time, and in some cases, even lead to an error. Perhaps the problem with RIGHT JOIN is that most requests are executed via LEFT JOIN, and as a result, optimization of requests with RIGHT JOIN is not optimal. In addition, LEFT JOIN is mostly used in practice. And the combination of LEFT and RIGHT JOIN should not be used at all because of their possible conflicting and opposite nature. Therefore, LEFT JOIN is the most optimal option for data selection.
</div>

<script>
  function openTab(evt, tabName) {
    var i, tabcontent, tablinks;
    
    tabcontent = document.getElementsByClassName("tab-content");
    for (i = 0; i < tabcontent.length; i++) {
      tabcontent[i].style.display = "none";
    }
    document.getElementById(tabName).style.display = "block";
  }
</script>