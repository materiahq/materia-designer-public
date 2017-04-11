Creating queries
================

Once your data structured, you can go in the tab `data` which contains all the development data and the default query for each entity.

![Screen data](/img/screen-data-query.png)

Query Type
----------

A query is an operation to retrieve, create, update, or delete data from the database.

A query has many type to handle everything:

* findAll - Retrieve many rows
* findOne - Retrieve one row
* create - create a row
* update - update one or many rows
* delete - delete one or many rows
* SQL - execute a SQL query
* Javascript - execute a Javascript function

Default Query
-------------

When you create an entity, there is automatically 5 default queries:

* list - Retrieve all rows (using pagination)
* get - Retrieve one row by its primary key
* create - Create a row
* update - Update a row
* delete - Delete a row

Query Builder
-------------

You can create your Query using the Query Builder:

![Create query](/img/gif/todo-queries.gif)

The query builder allow you to create a all type of queries. There is everything in the Query Builder to make your selection, your conditions, paginations and so on to retrieve the data you need.

**Input**

You can add a list of input which can be used in your query as parameters.

These input can be used in the condition of a query or in your custom Javascript or SQL query.

**Selection**

Only the field selected will be returned in the response. It allows you to accelerate your queries and get only the valuable data you'll use.

**Conditions**

To retrieve the data you need, you often need to add conditions to get only the data where the field `X` = `Y`.

There is multiple operator to execute all your conditions.

**Paginations**

When your queries returns hundreds of rows, it can take lots of seconds to send everything to your client. Pagination helps you to return just the `x` first rows to enable fast and reliable query.

Advanced queries
--------------

Sometimes, when your queries are really specific, it happens that the Query Builder is not enough and you need to write some code to make exactly what you want. It's possible using the query type `SQL` or `Javascript`. These queries can take parameters like other query type.

As the name says, the SQL type will let you write your SQL query while the Javascript type will let you write a Javascript functions which will be executed.

### SQL queries

SQL queries are stored in the JSON model as a string. They can handle parameters using the `:param` notation.

Currently only `SELECT` statement are supported.

e.g.

```
SELECT *
FROM product
WHERE price > :minPrice
  AND price < :maxPrice
```

This query take 2 parameters (minPrice and maxPrice), and return all product having a price between minPrice and maxPrice.

You can use SQL string concatenation to use the parameters inside a string

e.g.

```
SELECT *
FROM product
WHERE name LIKE '%' || :query || '%'
```

### Javascript queries

Javascript queries are stored in model files. They are simple ES6 classes:

```
module.exports = class ProductModel {
    constructor(entity, app) {
        this.entity = entity
        this.app = app
    }

    getProducts(params) {
        return this.entity.model.findAll({
            where: {
                price: {
                    $gt: params.minPrice,
                    $and: {
                        price: {
                            $lt: params.maxPrice
                        }
                    }
                }
            }
        })
    }

    search(params) {
        return this.entity.model.findAll({
            where: {
                name: {
                    $like: params.query
                }
            }
        })
    }
}
```

This class does the same things than the queries in the SQL chapter. It uses the syntaxe of Sequelize, the best ORM for Node.js.

Each Javascript query must return a promise which is resolved when the execution is a success. You can use [ES6 Promise object](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Promise) as explained in the Mozilla Developer Network.

#### Next step: [Managing endpoint](/docs/guide/endpoint)