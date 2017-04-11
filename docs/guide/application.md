Managing applications
=====================

A Materia application is a folder which contains all the files of your application. Most of these files are just simple JSON configuration files which are used to describe your backend.

Keep in mind that Materia designer automates a good part of how your application is architectured.


Application files
-----------------

The hierarchy of a minimal application is as follow:

```
.materia/
|  server.json
package.json
```

These 2 files are mandatory to launch a Materia application:

* **server.json** is used to define how to connect your database and how to host your server (host, port, ...)
* **package.json** is used to define npm dependencies in your application. Materia Designer is using this file to get the name of your application (and btw, the color of the icon)

The database configuration is now optional since the [August Release](https://github.com/webshell/materia-designer/releases/tag/0.2.0). You can just remove the key `database` from the file `server.json` and Materia will skip to connect the database.

All `json` files in the `server/models/` folder are descriptions of the entities you've created in Materia designer. They contains all information about the fields they may have, the relation between these entities, and all the queries you can execute on them.

Materia now supports addons: they are special npm package you can install using `npm install [package_name] --save` or `yarn install [package_name]` in the CLI. They can define their own entities, queries and endpoints to define new features for your application (e.g. emailing, user management etc.).

To learn more about these JSON file which describe your application, You can find [their specifications here](app/materia.json.md).

Example of the structure of a complete application:

```
.materia/
|  ids.json
|  server.json
|  addons.json
server/
|  controllers/
|  |  default.ctrl.js
|  |  customer.ctrl.js
|  |  ...
|  models/
|  |  queries/
|  |  |  customer.js
|  |  |  product.js
|  |  |  ...
|  |  customer.json
|  |  product.json
|  |  ...
|  permissions/
|  |  has-bought.js
|  api.json
|  permissions.json
web/
|  css/
|  |  main.css
|  |  ...
|  img/
|  |  logo.png
|  |  ...
|  js/
|  |  main.js
|  |  ...
|  index.html
.gitignore
package.json
webpack.config.js
```

Connect your application to your database
--------------------------------------

When creating a new application you can select a database (this step is optional but highly recommended). You can currently choose between:

* [PostgreSQL](https://www.postgresql.org/) - An object-relational database management system (ORDBMS) with an emphasis on extensibility and standards-compliance.
* [SQLite](https://www.sqlite.org/index.html) - An in-process library that implements a self-contained, serverless, zero-configuration, transactional SQL database engine.
* [MySQL](https://www.mysql.org) - MySQL is an open-source relational database management system (RDBMS)

SQLite stores everything in a file and is easier to start with as it doesn't require any installation to work. It just works out of the box. It's limited for small or medium database as it is harder to scale with this DB and as you can't connect to the DB from another server using a TCP connection, the Live mode of Materia Designer cannot work for SQLite.

PostgreSQL and MySQL are similar as you have a server you can connect to. You can install PostgreSQL in the [PostgreSQL Download](https://www.postgresql.org/download/) page and MySQL in the [MySQL Download]() page.

Application list
----------------

At any time, you can use the <i class="fa fa-th"></i> icon at the left on your application name to open the application sidenav.

In this sidenav, you can switch application:

![App switch](/img/gif/app-swap.gif)

You can create a new application using the <i class="fa fa-plus"></i> icon in the bottom of the application sidenav.

#### Next step: [Starting/stopping the server](/docs/guide/server)