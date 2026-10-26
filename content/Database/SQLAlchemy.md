---
title: SQLAlchemy
publish: true
date created: 2026-10-26
tags:
  - database
  - python
---
SQLAlchemy is a Python library that lets your Python application communicate with a database. It supports databases such as PostgreSQL, MySQL, and SQLite.

In your Agno database expert project, SQLAlchemy acts as the connection between your Python code and the actual database.

## 1. Where does SQLAlchemy fit?

Agno Expert Agent

Decides what information it needs

Python tool

Receives the agent's requested operation

SQLAlchemy

Manages the database connection and executes SQL

PostgreSQL

Executes the query and returns the result

For example, the agent might decide it needs to retrieve a customer's orders. SQLAlchemy helps your application send the corresponding SQL query to PostgreSQL and receive the results.

## 2. How do you use SQLAlchemy?

First, install it along with a PostgreSQL driver:

```
pip install sqlalchemy "psycopg[binary]"
```

Then create a connection engine:

```
from sqlalchemy import create_engine, textengine = create_engine(    "postgresql+psycopg://user:password@localhost/mydb")
```

Here, `create_engine()` configures how your application connects to PostgreSQL. It doesn't necessarily establish the network connection immediately; connections are typically opened when needed.

Now you can execute a query:

```
with engine.connect() as connection:    result = connection.execute(        text("SELECT name FROM customers")    )    for row in result:        print(row.name)
```

This executes SQL and prints the customer names returned by the database.

Notice that you're still writing SQL yourself. SQLAlchemy doesn't require you to stop using SQL.

## 3. Does SQLAlchemy replace SQL?

No. It gives you two main ways to work with databases.

SQL execution

You write SQL statements, and SQLAlchemy executes them.

```
connection.execute(    text("SELECT * FROM customers WHERE id = :id"),    {"id": 5},)
```

Useful for database expert agents that need to execute SQL generated from natural-language requests. Parameters help prevent SQL injection for values.

ORM (Object-Relational Mapper)

You work with Python classes and objects instead of writing every SQL statement manually.

```
customer = session.get(Customer, 5)print(customer.name)
```

Useful when your application models database tables as Python classes.

SQLAlchemy supports both approaches. The ORM is optional; you can use SQLAlchemy without defining any ORM models.

## 4. Why does Agno use it?

In the database context provider, you pass an engine such as:

```
db = DatabaseContextProvider(    sql_engine=write_engine,    readonly_engine=read_engine,    schema="public",)
```

Agno uses these engines to provide database operations to the agent. SQLAlchemy handles the underlying connections and SQL execution.

One important distinction: SQLAlchemy itself does not decide whether a refund is permitted, whether a user is authorized, or whether an administrator must approve a deletion. Those are responsibilities of your application logic and database permissions.

In short: Agno gives your AI agent database tools, SQLAlchemy connects those tools to the database, and PostgreSQL stores and manages the actual data.


## What is an Engine?

An Engine is the object SQLAlchemy uses to manage connections to your database and execute SQL.

Imagine PostgreSQL is a server containing your data. Your Python application needs a way to communicate with it. The engine provides that connection infrastructure.

Your Python application

Requests data

SQLAlchemy Engine

Manages connections and connection pooling

PostgreSQL

Executes SQL and returns data

### How do you create an engine?

```
from sqlalchemy import create_engineengine = create_engine(    "postgresql+psycopg://user:password@localhost/mydb")
```

Let's break down the connection URL:

|Part|Meaning|
|---|---|
|`postgresql`|The database type|
|`psycopg`|The Python driver used to communicate with PostgreSQL|
|`user:password`|Database credentials|
|`localhost`|Where the database server runs|
|`mydb`|The database name|

The engine also manages a connection pool. Rather than establishing a brand-new database connection for every query, SQLAlchemy can reuse existing connections.

One subtle detail: creating the engine usually doesn't immediately connect to the database. A connection is typically established when you first execute a query or otherwise request a connection.

### Why does Agno have two engines?

In your database expert project, you might see:

```
db = DatabaseContextProvider(    sql_engine=write_engine,    readonly_engine=read_engine,)
```

You can think of these as two different access paths:

- `readonly_engine` connects using credentials intended for reading.
    
- `sql_engine` connects using credentials that permit the required modifications.
    

Both are SQLAlchemy engines, but they can use different database users and permissions. The database permissions—not the variable names—determine what each connection is actually allowed to do.

---
[[Database]]
[[Python]]