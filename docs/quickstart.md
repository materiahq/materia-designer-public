Quickstart
==========

This quickstart is a guide for installing and creating your first Materia application: A basic TODO application.


I - Install Materia
-------------------

Go to the [download page](https://github.com/webshell/materia-designer/releases) to grab the latest version of Materia for your operating system (available for Windows, Mac), then install it.

You're now ready to start Materia Designer!


II - Create your first Materia application
------------------------------------------

To create your first application: you'll need an application directory (an empty folder somewhere on your filesystem) and the information to connect to your PostgreSQL database. For this, you'll need a PostgreSQL database installed and running.

**Since 0.2.0**: You can also choose SQLite which require no installation as SQLite is already bundled in Materia Server.

![Create app](/img/gif/todo-create-app.gif)

III - Create an entity
---------------------

Go in **Entities** in the side menu. This view is the main view to architecture your data structures. Let's create a first entity **todo** with 2 fields

	* **done** | type boolean | default false
	* **task** | type text | required

Note: The field `id` is already created for us as the primary key.

![Quickstart todo](/img/gif/todo-entities.gif)

In the **Data** tab in the right sidenav, you can see the default queries.
On each entity, you always have default queries to fetch one, fetch all, create, update, delete data in the entity.

![data todo](/img/gif/todo-data.gif)


IV - Create an endpoint
-----------------------

Go in **API** in the side menu. Your API is the set of all the HTTP URL available in your web server. These endpoint usually sends back JSON to communicate with your frontend (a web page, a mobile application, a game etc...). 

In the following animation, we'll create an endpoint to fetch all **todo** using the default query **list**

![endpoint todo](/img/gif/todo-api.gif)

Once your endpoint `GET /api/todos` is configured and executed, it executes the **list** query of the entity **Todo** and return its response in JSON.

You can repeat this step to create others endpoints:

* `GET /api/todos/:id` => findOne

* `POST /api/todos` => create

* `PUT /api/todos/:id` => update

* `DELETE /api/todos/:id` => delete


V - List your TODOs in a website
--------------------------------

We will use the endpoint we've created to display all todos on a web pages.

![todo website](/img/gif/todo-website.gif)

Go in `Web` in the side menu, create the default view and edit the `index.html` file to set this code inside:

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>Todo with Materia</title>
	</head>
	<body>
		<ul id="todos">
		</ul>
		<script type="text/javascript">
$('document').ready(function() {
	$.get('https://localhost:8080/api/todos')
		.success(function(data) {
			let cssClass = ''
			if (data.done) {
				cssClass = ' class="done"'
			}
			$('ul#todos')
				.append(`<li${cssClass}>
					${data.task}
				</li>`)
	})
})
		</script>
		<style>
li.done {
	text-decoration: line-through;
}
		</style>
	</body>
</html>
```

That's all you need to list your todos with jQuery. Of course, it works with others framework as Angular or React.

VI - TODO application finished using Angular.js and Angular Material
--------------------------------------------------------------------

In this example, we've chosen Angular.js but as explained above, it can be really any Javascript framework.

To have a nice UI, we've chosen Angular Material which is easy to use and have all the component required for the Todo applications.

![Todo final application](/img/gif/todo-environment.gif)

The complete application source code is [available here](https://github.com/thyb/materia-todo). 

You can use `git` to clone the repository:

```
git clone git@github.com:thyb/materia-todo.git
```

Then you can open the folder `materia-todo` with Materia Designer to see the result!

This application include:

* Toggle todo done
* Remove done todos
* Create new todo


Next step
---------

* [Guide](/docs/guide/install) - In-depth guide to use Materia.
