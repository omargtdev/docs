# Similitudes with SQL
Well, this is an explanation and some tips to help you understand better
NoSQL if you have knowledgeable about SQL.

## Concept
The way that him stores data is with BSON (Binary JSON), it means, like
JSON entities or files.

## Database
An database in mongo is like a "container" for one or more collections of documents (we'll see following).
If we wanna create an database we need specify at least one collection.

- To list databases it would be with `show dbs` statement.
- To create an database, particulary you just execute `use *<db-name>*`,
but you need to create at least one collection to make "save" that database.
- When you select your database to use, the keyword to interacte with it,
always be `db`.

## Collection (Table)
An collection is basically like a table but without an specific structure.
For example, I have the following table:

```sql
USE MyDatabase;

CREATE TABLE MyTable (
  id INT PRIMARY KEY AUTO_INCREMENT,
  description VARCHAR(20) NOT NULL
  otherField VARCHA(50)
); 

INSERT INTO MyTable (description, otherField) VALUES ('Some item', NULL);
```

For every record of the table, you have the same quantity of columns, 
but with mongo, in a collection you can have or not the same properties
for every record or rather document, but you should have it for ensure data integritiy.

```js
use MyDatabase

db.createCollection("MyTable")

db.MyTable.insertOne(
  {
    description: "Some item",
    otherFild: null
  }
)

db.MyTable.insertOne(
  {
    description: "Some item"
  }
)
```

## Document (Register)
The documents it's not more than registers in an collection,  like a record basically. It would be similar to JS object. 

## Insert documents (Insert into)
To insert documents to an collection, only specify the database to use, then
specify the collection to add with the functions `insertOne` or `insertMany`.

- `insertOne` for insert only one object
- `insertMany` for insert various, in an array

```js
use MyDatabase

db.createCollection("products")

db.products.insertOne({ name: "chocolatey", price: 2.50 })
db.products.insertMany([
  { name: "book", price: 5.50 },
  { name: "apple", price: 1.50 }
])
```
## Datatypes
Well, the datatypes in mongo are the same types that are in js practically.

```js
{
  name: "guitar", // string
  price: 2.50, // number (int/float)
  registerDate: new Date("2022-02-12"), // date
  hasExpired: false, // boolean
  gift: null, // null
  tags: ["6 strings", "electric", "instrument"], // array<type>[]
  brand: { // object
     companyName: "Gibson",
     address: "Av. SiempreViva 123 EE.UU",
     city: "EE.UU",
  }
} 
```

## Find (Select/Where)
This is the method to be able to list or read the records from some
collection. You can add filters to it (like where).

## Sort (Order by)
You can use `sort({ field: <1|-1> })` to order documents from descending
or ascending way like `ORDER BY` in sql.

Where:
-  1 = ascending
- -1 = descending

```js
// Get the list of products order by name in ascending way
db.products.find({ name: 1 })

// Get the list of products order by name in descending way and
// price in ascending way
db.products.find({ name: -1, price: 1 })
```

##  Limit (Limit | Top)
Get the limit of records, like TOP in SQL Server or LIMIT in MySQL, with
`limit()` method. It requires the count of records to fetch.

```js
// Get the first two records of products
db.products.find().limit(2)
```
