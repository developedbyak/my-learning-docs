# PostgreSQL

<P>Open Source Relational Database Management System (RDBMS)</P>

> Click :star:if you like the project and follow [@developedbyak](https://twitter.com/developedbyak) for more updates.

### Table of Contents

| No. | Topics                                                                                                             |
| --- | ------------------------------------------------------------------------------------------------------------------ |
| 1   | [Installation](#installation)                                                                                      |
| 2   | [Introduction to Postgres](#introduction-to-postgres)                                                              |
| 3   | [Understand how to use keys, Postgres types and Keywords](#understand-how-to-use-keys-postgres-types-and-keywords) |
| 4   | [Use pgAdmin to CREATE a TABLE](#use-pgadmin-to-create-a-table)                                                    |

### Installation

1. [Postgres Server](https://www.postgresql.org/download/) for local development.
2. [pgAdmin]() GUI (Graphical User Interface) for PostgreSQL.

### Introduction to Postgres

PostgreSQL is a powerful open-source relational database management system (RDBMS) that uses and extends the SQL language. It is known for its reliability, scalability, and robustness, making it a popular choice for many applications, from small-scale web applications to large-scale enterprise systems.

PostgreSQL is free to use and can run on a variety of operating systems, including Windows, macOS, and Linux. It also supports a wide range of advanced features such as JSON support, full-text search, and geospatial data processing, which make it an attractive choice for developers and organizations with complex data needs.

**Basic syntax for postgreSQL**

_index.js_

```js
import Client from "pg"

const db = new Client(
    user: "username",
    host: "localhost",
    database: "mydatabase",
    password: "password",
    port: 5432,
)

db.connect();

db.query("SELECT * FROM USERS", (err, res) => {
    if (err) {
        console.error("Error executing query ", err.stack);
    } else {
        console.log("User Data: "+ res.rows);
    }

    db.end();
})
```

**[⬆ Back to Top](#table-of-contents)**

### Understand how to use keys, Postgres types and Keywords

To create a table in postgreSQL

```sql
CREATE TABLE friends (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    is_cool BOOLEAN
);
```

Let's understand this:<br>

-   `CREATE TABLE` keyword to create a table.
-   `friends` table name.
-   `id` it's a `primary key` this ensure that every data has an unique id.
-   `SERIAL` keyword will add `id automatically` for the next data so we don't have to add `id` manually.
-   `name` here the `VARCHAR` stands for `Variable Character` and `(50)` will limit the data size upto a maximum of 50 characters but if your name only take upto 4 character it will automatically decrease the size so you can efficiently manage your storage.
-   You can also use `TEXT` datatypes it's same as `VARCHAR` but you don't have to set a limit and it can also automatically use the amount of character your name needs to be.
-   `age` saving age as an `Integer (INT)` datatype.
-   `is_cool` it's using a `BOOLEAN` datatype means binary option only `true` & `false`.

**To Learn More About Data Types:**

https://www.postgresql.org/docs/current/datatype.html
<br>

**[⬆ Back to Top](#table-of-contents)**

### Use pgAdmin to CREATE a TABLE

Open pgAdmin application on your pc:

-   Now on the left side when you click to servers it will again
    ask you password to enter something like this :

```
Please enter the password for the user 'postgres' to connect the server - "PostgreSQL 16"
```

-   In my case it was admin which i set up when i install the pgAdmin.
-   Check save password option. And click ok.
-   Now under PostgreSQL 16 or whatever version you are using you will get some drop-down options -

> Databases<br>
> Login/Group Roles<br>
> Tablespaces<br>
> pgAgent Jobs<br>

-   Now expand the Databases and you will see a default database named `postgres`.
-   But we won't use that so to create a new database right click `Databases - Create - Database...`
-   Give it a name.
-   Owner will be default `postgres`.
-   And just click `save`.

**Now to Create a New Table**

-   Expand `world - Schemas - Tables` You will see the table is empty.
-   Now select the database world and press `Alt + Shift + Q` or you can just click the icon it will be on navbar.
-   Now we can just write out SQL Code here 😉 using cli is always feels good right ?.

```sql
CREATE TABLE capitals (
	id SERIAL PRIMARY KEY,
	country VARCHAR(45),
	capital VARCHAR(45)    --> note : no comma
);
```

-   Make sure to put a semicolon at the end which is important in SQL .
-   Last field of the table should not have a comma its not a javascript object okay.
-   Now run this code by pressing `F5` or the run button on the pgAdmin.

**If successfull you will get this message:**

```
CREATE TABLE

Query returned successfully in 60 msec.
```

-   Now to go Tables in Schema and right click refresh it will show the table.
-   Then Right click on capitals and View/Edit Data then All Rows.

**Or you can run this command on pgAdmin:**

```sql
SELECT * FROM public.capitals
ORDER BY id ASC
```

-   Now you can see the table we created but it doesn't contain any data at the moment.
-   If you click capitals and View/Edit Data then all other options it will show will the codes on pgAdmins Query area.

**For Example**

-   First 100 Rows

```sql
SELECT * FROM public.capitals
ORDER BY id ASC LIMIT 100
```

-   Last 100 Rows

```sql
SELECT * FROM public.capitals
ORDER BY id DESC LIMIT 100
```

**Currently our table is empty so let's see how to import data from a `.csv` file.**

csv stands for - comma separated values

**To import data**

-   Right click on table - capitals - Import/Export Data

---

**If you face this error:**

```
Utility file not found. Please correct the Binary Path in the Preferences dialog
```

-   Inside `pgAdmin` Open: `File - Preferences - Paths - Binary paths`
-   Check PostgreSQL Binary Path , check set as default to the version you are using .
-   and most importantly add the Binary Path in my case it was - `C:\Program Files\PostgreSQL\16\bin`
-   now save it .

---

-   Now a new tab will open
-   Select Import and Filename (The capitals.csv is also uploaded in github so download it)
-   Format should be .csv
-   Now to to Options and Make sure Header option is enabled. This will tell the pgAdmin that out first row is not data and its a header for the data.
-   now click okay and you will see green popups means all is okay !.
