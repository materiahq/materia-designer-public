# api.json

The file `api.json` contains the informations about your endpoints.

```json
[
	{
		"method": "get",
		"url": "/my/endpoint",
		"query": {
			"entity": "addon",
			"id": "list"
		}
	},
	{
		"method": "get",
		"url": "/my/js_endpoint",
		"file": "custom",
		"ext": "js"
	},
	...
]
```

---

## method

HTTP method, can be `get`, `post`, `put`, `delete`.

`"method": "get"`

## url

HTTP url relative to the api path.

`"url": "/my/endpoint"`

## query

This links the endpoint to the query `id` from the entity `entity`

```
"query": {
	"entity": "addon",
	"id": "search"
}
```


## controller

You can use a Javascript controller to define the behavior of an endpoint. A controller is a Javascript ES6 class with methods which can be linked to an endpoint

These controllers must be in `server/controllers/`.

```
"controller": "default",
"action": "listAll"
```

for this config to work, you need a controller `server/controllers/default.ctrl.js` which contains something like:

```javascript
module.exports = class DefaultCtrl {
	constructor(app) { this.app = app; }

	listAll(req, res, next) {
		//todo...
		res.status(200).send({'hello': 'world'})
	}
}
```