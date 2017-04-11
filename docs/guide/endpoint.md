Creating endpoints
==================

Your API is a set of endpoints which is defined by a method (`GET`, `POST`, `PUT`, `DELETE` or `PATCH`) and a url (e.g. `/users/active`) and has a type (**Query** or **Code**).

If your endpoint has the type **Query**, it means that when you call the endpoint, a query will be executed and its result will be returned.

![api](/img/gif/todo-api.gif)

If your endpoint has the type set to `Code`, it means that when you call the endpoint, a Javascript function will be executed and return a Promise or use `res` to send data (e.g. `res.status(200).send({data: 42})`) 

Creating endpoints in Javascript
================================

Using Javascript, you are free to make some HTTP calls, make multiple database queries and so on.
The only restriction: you need to return a promise or use `res` to send data.

A Javascript endpoint can be defined like this:

```js
class DefaultController {
	constructor(app) { this.app = app }

	helloWorld(req, res, next) {
		return res.status(200).send({ hello: 'world' })
	}

	helloWorld2(req, res, next) { //same as helloWorld but can be chained as it uses the promise syntaxe
		return Promise.resolve({
			hello: 'world'
		})
	}

	helloWorld3(req, res, next) { //same as helloWorld but can be chained as it uses next()
		res.status(200).send({ hello: 'world' })
		next()
	}
}
```

`app` is an App object defined in Materia Server. From this object, you can access endpoints, entities, queries, permissions, database settings and server settings. You can use it with `this.app` in your endpoints method.

`req`, `res` and `next` are Express parameters used in endpoints. 

* `req` will give you all information about the request and the parameters.
* `res` can be used send the response and handle headers and status code.
* `next` is optional and can be used to chain middleware.

You are also free to use any package of [NPM](https://www.npmjs.com) by installing them in your application directory and using them in your endpoint like in any Node.js application:

```javascript
var myModule = require('moduleName')
//then, use myModule...
```

Call and orchestrate existing Materia queries from a Javascript endpoint
---------------------------------------

You can use `this.app` in the method of your model to execute and orchestrate your queries execution:

```js
class ProductController {
	constructor(app) {
		this.app = app
		this.product = this.app.entities.get('product')
	}

	buy(req, res, next) {
		return this.product.getQuery('isAvailable')
			.run(req.body.productId)
			.then(isAvailable => {
				if (isAvailable) {
					return this.product.getQuery('buy')
						.run(req.body.productId)
				}
				else { return Promise.reject(new Error('This product is not available!')) }
			})
	}
}
```

#### Next step: [Serving static content](/docs/guide/static-content)

