# Room: Database SQL Basics

**Path:** Operating Systems Basics

**Date:** August 2026

**Difficulty:** Easy

---

## Objective

Understand the fundamentals of databases and SQL: why databases are used, how information is organized into tables, rows, and columns, and how to write basic SQL queries to retrieve, filter, and sort data. The room uses a café order example throughout.

---

## Key Concepts

* **Database:** An organized collection of information stored on a computer, structured for fast searching, filtering, and reporting.
* **Table:** A collection of related records, similar to a spreadsheet.
* **Column:** Describes one type of information stored (e.g. drink, price, time).
* **Row:** A single complete record (e.g. one customer order).
* **SQL (Structured Query Language):** The language used to communicate with databases.
* **Query:** A request for information from a database — it retrieves, filters, or sorts data without changing it.

---

# Task 1: Introduction

## Scenario

A busy café records every customer order. Writing orders in a notebook works at first, but as the number of orders grows, answering questions like *"How many coffees were sold today?"* or *"Which drink sells the most?"* becomes slow and difficult to do manually. This is where databases help.

## What Happens to Data?

Computers process information while running, but important information must still exist after the computer is turned off. Databases provide a reliable way to store and retrieve that information whenever needed.

## Why Businesses Use Databases

As businesses grow, more information must be stored, more records are created, and searching through files becomes slower. Databases provide fast searching, easy organization, efficient storage, and quick reporting.

---

# Task 2: Understanding Tables, Rows, and Columns

## What Is a Database?

A database is an organized collection of information stored on a computer — like a digital notebook that never runs out of pages, stores large amounts of data, finds information quickly, and allows sorting and filtering.

## Information Is Stored in Tables

Databases organize information into tables, similar to a spreadsheet.

### Columns

Columns describe the type of information being stored (e.g. Order ID, Drink, Price, Time). Each column contains one type of data.

### Rows

Rows represent individual records. Each row contains all the information about one item.

Example — one customer order:

| Order ID | Drink | Price | Time |
|---|---|---|---|
| 1 | Coffee | 3.50 | 09:15 |

## Café Example

Each customer order creates a new row:

| Order ID | Drink | Price |
|---|---|---|
| 1 | Coffee | 3.50 |
| 2 | Tea | 2.00 |
| 3 | Latte | 4.50 |

Three orders = three rows.

### Adding & Removing Records

* A new order → a new row is added.
* A deleted order → only that row is removed; the rest of the table stays unchanged.

## Asking Questions with SQL

**SQL** stands for **Structured Query Language** and is used to communicate with databases. Instead of manually searching through records, we ask the database questions — called **queries**.

A query retrieves, filters, and sorts data, but does not automatically change what's stored — it simply displays results.

## Answer Check

**Q) Inside databases, what is the term for the "spreadsheets" that store information?**
A) `table`

---

# Task 3: Writing Your First SQL Query

## Available Tables

The café database contains two tables:

**Orders** — `id`, `drink`, `price`, `time`
**Menu** — `drink`, `price`

## Core SQL Keywords

`SELECT`, `FROM`, `WHERE`, `ORDER BY`

## Step 1: View Everything (SELECT + FROM)

```sql
SELECT * FROM Orders;
```

`*` means all columns. The database opens the `Orders` table, retrieves every column, and displays every row.

**Breakdown:** `SELECT` specifies what data to display, `*` means all columns, `FROM` specifies which table to use, and `Orders` is the table being queried.

## Step 2: Select Specific Columns

```sql
SELECT drink, price FROM Orders;
```

Only the `drink` and `price` columns appear; other columns remain hidden. This gives cleaner output, faster queries, and easier analysis.

## Step 3: Filter Results (WHERE)

```sql
SELECT * FROM Orders
WHERE drink = 'Coffee';
```

Only rows where `drink = Coffee` are displayed. The database checks every row — if the condition is true, the row is displayed; if false, it's ignored.

To view available drinks:

```sql
SELECT * FROM Menu;
```

## Step 4: Sort Results (ORDER BY)

Ascending (default):

```sql
SELECT * FROM Orders
ORDER BY price;
```

Prices appear lowest → highest.

Descending:

```sql
SELECT * FROM Orders
ORDER BY price DESC;
```

Prices appear highest → lowest. `DESC` means descending order.

## Step 5: Combine Filtering and Sorting

```sql
SELECT * FROM Orders
WHERE drink = 'Coffee'
ORDER BY price DESC;
```

This finds Coffee orders, sorts them from highest to lowest price, and displays the results. SQL commands can be combined to answer more complex questions.

## Answer Check

**Q) When all orders were displayed, how many rows were returned?**
A) `50`

**Q) When orders were sorted by price from cheapest to most expensive, which drink appeared first?**
A) `Tea`

**Q) When the menu was sorted by price from most expensive to cheapest, which drink appeared first?**
A) `Latte`

---

# Task 4: Conclusion

This room introduced the foundations of databases and SQL. Using a café example, it covered how information is stored and how SQL can retrieve useful information from tables.

---

# Key Terminology

* **Database:** Stores information in an organized manner.
* **Table:** A collection of related records.
* **Column:** Stores one type of information (e.g. Price, Drink, Time).
* **Row:** Represents one complete record (e.g. one café order).
* **Query:** A request for information from a database.
* **SQL:** The language used to communicate with databases.
* **`SELECT`:** Choose what information to display (e.g. `SELECT drink`).
* **`FROM`:** Choose the table (e.g. `FROM Orders`).
* **`WHERE`:** Filter records (e.g. `WHERE drink = 'Coffee'`).
* **`ORDER BY`:** Sort results (e.g. `ORDER BY price`).

---

# Key Takeaways

* Databases organize information into **tables**, made up of **columns** (types of data) and **rows** (individual records).
* **SQL** lets you ask questions of a database — called **queries** — without permanently changing the stored data.
* `SELECT` and `FROM` retrieve data from a table; `SELECT *` retrieves all columns, while naming specific columns keeps output cleaner.
* `WHERE` filters rows based on a condition; `ORDER BY` sorts results (ascending by default, `DESC` for descending).
* SQL keywords can be **combined** — e.g. filtering with `WHERE` and sorting with `ORDER BY` in the same query — to answer more complex questions.
* Databases and SQL form the foundation of modern applications, enabling fast storage, search, filtering, and reporting at scale.

---

## What I Learned

This room gave me a clear, practical introduction to how databases and SQL work, using a relatable café example. Before this room, I understood databases only in the abstract — as "where an app stores its data" — but I hadn't connected that to the actual structure of tables, rows, and columns, or how SQL is used to interact with them.

I learned that a table is essentially a structured spreadsheet, where each column defines a type of data (like `drink` or `price`) and each row represents one complete record (like a single order). This made it much clearer why databases scale so much better than notebooks or flat files as the amount of data grows.

Writing my first SQL queries was the most useful part. I practiced retrieving everything with `SELECT * FROM Orders;`, narrowing results down to specific columns, filtering rows with `WHERE`, and sorting results with `ORDER BY` (both ascending and descending with `DESC`). Combining `WHERE` and `ORDER BY` in a single query — filtering for Coffee orders and then sorting them by price — showed me how SQL statements build on each other to answer more specific, real-world questions. This gave me a solid foundation before moving on to more advanced SQL topics like joins and data modification.