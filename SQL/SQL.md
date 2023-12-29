# SQL

### To Create a Table in SQL : (CREATE SCHEMA)

```sql
// Schema for our PRODUCTS Colllection
CREATE TABLE PRODUCTS (
  	ID INT NOT NULL,
  	NAME STRING,
  	PRICE MONEY,
  	PRIMARY KEY (ID)
)
```

### The SQL INSERT INTO Statement (CREATE)

 two ways:

```sql
// 1st way
INSERT INTO PRODUCTS (ID, NAME, PRICE)
VALUES (1, "Pen", 1.20)

// 2nd way
INSERT INTO PRODUCTS
VALUES (1, "Pen", 1.20)
```

### TO READ DATA

```sql
// to see all data
SELECT * FROM PRODUCTS

// to select specific data
SELECT NAME, PRICE FROM PRODUCTS

// SQL WHERE
SELECT * FROM PRODUCTS
WHERE ID = 2;
```

### Updating Single Values and Adding Columns

```sql
// UPDATE
UPDATE PRODUCTS
SET PRICE = 0.80
WHERE ID = 2;

// ALTER TABLE : This is when you want to add a new column in your current table
ALTER TABLE PRODUCTS
ADD QUANTITY INT;
```

### Delete

```sql
DELETE from PRODUCTS
WHERE ID=1;
```

### Relation Between Tables

```sql
CREATE TABLE ORDERS (
      ID INT NOT NULL,
  	ORDER_NUMBER INT,
  	USER_ID INT,
  	PRODUCT_ID INT,
  	PRIMARY KEY (ID)
  	FOREIGN KEY (USER_ID) REFERENCES USERS(ID),
  	FOREIGN KEY (PRODUCT_ID) REFERENCES PRODUCTS(ID)
)
```

Let’s break it down :

1. First we are creating the **ORDERS** table.
2. We set **ID, ORDER_NUMBER, USER_ID, PRODUCT_ID**.
3. **PRIMARY KEY** is the **ID** of the current table that we are creating.
4. **FOREIGN KEY (USER_ID) REFERENCES USERS(ID)**
here we are adding a relationship between ORDERS table and USERS table
the ID in USERS(ID) is the PRIMARY KEY of the USERS table.
5. **FOREIGN KEY (PRODUCT_ID) REFERENCES PRODUCTS(ID)**
here we are adding a relationship between ORDERS table and PRODUCTS table
the ID in PRODUCTS(ID) is the PRIMARY KEY of the PRODUCTS table.

```sql
INSERT into ORDERS
VALUES (1, 4362, 1, 3) // ID, order_id, user_id, product_id
```

### INNER JOIN

```sql
SELECT ORDERS.ORDER_NUMBER, USERS.NAME
FROM ORDERS
INNER JOIN USERS ON ORDERS.USER_ID = USERS.ID

---------------------------------

SELECT ORDERS.ID, ORDERS.ORDER_NUMBER, USERS.NAME, PRODUCTS.NAME, PRODUCTS.PRICE
FROM ORDERS
INNER JOIN USERS ON ORDERS.USER_ID = USERS.ID
INNER JOIN PRODUCTS ON ORDERS.PRODUCT_ID = PRODUCTS.ID
```