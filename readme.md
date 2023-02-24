## CRUD APIs

- Create
- Read
- Update
- Delete

### Technologies

- ExpressJS Framework (NodeJS backend)
- Splite(Database)

### intro

Create CURD Operations on Products

### Product

- Product ID
- Name
- Price
- Description

### Sample Data
| Product_id| Name|Price| Description|
|------|-----------|------|----------|
|1 | TShirt|900|Printed TShirt|
|2 | Airpods|3000|Apple Clone|


## SQL Queries

1. Create Table

```sql
CREATE TABLE "products" (
	"product_id"	INTEGER,
	"name"	TEXT,
	"price"	INTEGER,
	"description"	TEXT,
	PRIMARY KEY("product_id" AUTOINCREMENT)
);
```

2.Create Procucts

```sql
INSERT INTO products(
    name,
    price,description
) VALUES(
    "TShirt",
    900,
    "Printed TShirt"
)
```

3. Get All Products from the table

```sql
SELECT * from products 

```

4. Get Single Product info by productId(Example is id `2`)

```sql
SELECT * from products WHERE product_id = 2

```

5. Update products based on Product ID (example id is `1`)

```sql
UPDATE products
set
price
WHERE
product_id =1
```

6. Delete the product from table based on products id
(example id is `4`)

```sql
DELETE from products WHERE product_id=4
```

## Connecting SQLite DB in ExpressJS

we are using  https://github.com/TryGhost/node-sqlite3

Connecting sqlite DB using sqlite3
library by following

```JS
const sqlConnector = require('sqlite3').verbose();

const database = new sqlConnector.Database("./path-for-database.db",
sqlconnector.OPEN_READWRITE, (error) =>{
    if (error) {
        console.log(error)
    }
})
```

Run sql queries for just create, update and delete

```js
database.ecec(SQL_QUERY,(error,success) => {})
```
For Get rows from DB

1. For Single row
```js

database.get(`SELECT * from products WHERE product_id=${2}`, (error,row) =>{


if(error) {
    // show some meaning for message
} else {
    // use the row value 
}
})
```


2. For Multiple rows

```js
database.all(`SELECT * from products`,(error,rows) =>{

})
```

### ExpressJS

we use expressjs mainly for creating server
(mostly handing request and response)

```js
const express = require("express");
const bodyParser = require("body-parser");
const app = express();

// For Handling JSON request body 
app.use(bodyParser.json () )

//Listen server on any available port
app.listen(3000);
```

Handling Request and Response in ExpressJS

```js
//Every route will have a requestand accept a response
app.get(ROUTE_FOR_REQUEST, function(request,response) {})

// Another example
const handleMyRequest = function(req,res) {

}
app.get(PATH_FOR_ROUTE,handleMyRequest)
// Request 5 tickets (150) - Each ticket Price is 50
```


## Handling CRUD Operations in any SERVER

- Create(POST)
- Read(GET)
- Update(PUT)
- Delete(DELETE)

## HTTP Methods

|Method|operation|SQL|
|----|------=-|-------|
|POST| Create| INSERT|
|GET | Read | SELECT|
|PUT  | Update|UPDATE|
|Delete| Delete|DELETE


### Define CRUD Operations in ExpressJS Routes

1. Create
```js
function handlePost(req,res) {}
app.post('/',handlePost)
```

2. Read
```js
const handleGet = (req,res) => {}
app.get('/',handleGet)
```

3. Update

```js
// some-files.js
const handlePut = function(req,res) {

}

module.exports = {
    handle.Put: handlePut
}
const methods= require("some-files.js")
app.put('/', method.handlePut)
```

4. Delete

```js
app.delete('/',(req,res) => {})
```
