MySQL Python Class
===========

## Description

**Python MySQL class** helps the python developers to connect with MySQL and use queries like: SELECT (one and more conditions), INSERT, UPDATE, DELETE in an easy and fast way.

## Usage

To start using the **Python MySQL class** you need to import the class and initialize with 4 required parameters: `host`, `user`, `password`, `database`

```python
from mysql-python import MysqlPython

connect_mysql = MysqlPython('host.ip.address', 'user', 'password', 'database')
```

#### Select one condition

If you want to obtain information from one table and use one condition, you could use `select` function where `args` argument is for referencing the columns you need to obtain.

```python
  conditional_query = 'car_make = %s '

  result = connect_mysql.select('car', conditional_query, 'id_car', 'car_text', car_make='nissan')
```

**Result:**
  The function return a list or empty list in case of not find nothing.

---

#### Select more than one condition

In case you have need to obtain information with more than one condition, you could use the `select_advanced`function, where the columns you need to obtain are referenced by `args` and the conditionals are referenced by `tuples`

```python
  sql_query = 'SELECT C.cylinder FROM car C WHERE C.car_make = %s AND C.car_model = %s'

  result = connect_mysql.select_advanced(sql_query, ('car_make', 'nissan'),('car_model','altima'))
```

*Note: Inside the `sql_advanced` function the order of the parameters matters, so the `tuples` should have the order of the query.*

**Result:**
  The function return a list or empty list in case of not find nothing.

---

#### Insert data

Inserting data is really simple and intuitive, where we are going to reference the column and the values

```python
  result = connect_msyql.insert('car', car_make='ford', car_model='escort', car_year='2005')
```

**Result:**
The function return the last row id was inserted.

---

### Update data

To update data just needs the table, conditional query and specify the columns you want update

```python
conditional_query = 'car_make = %s'

result = connect_mysql.update('car_table', conditional_query, 'nissan', car_model='escort', car_year='2005')
```

**Result:**
This function return the amount of rows updated.

---

#### Delete data

Delete data is really simple like insert, just reference the column as condition and table.

```python
  conditional_query = 'car_make = %s'

  result = connect_mysql.delete('car', conditional_query, 'nissan')
```

**Result:**
This function return the amount of rows deleted.

## Requirements

MySQL-python >= 1.2.5
