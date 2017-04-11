.materia/server.json
===================

The file `server.json` contains the configuration to connect with your server and database.

```json
{
	"dev": {
		"web": {
			"host": "localhost",
			"port": 8080
		},
		"database": {
			"type": "postgres",
			"host": "localhost",
			"port": 5432,
			"database": "materia",
			"username": "postgres",
			"password": "zxcvbn123"
		}
	},
	"prod": {
		"web": {
			"host": "localhost",
			"port": 8085
		},
		"database": {
			"type": "postgres",
			"host": "127.0.0.1",
			"port": 5432,
			"database": "database-name",
			"username": "postgres",
			"password": "your-password",
		},
		"git": {
			"remote": "origin",
			"branch": "master"
		}
	}
}
```

As you can see, there is a setting for development and a setting for the production.

This file is automatically filled by Materia Designer when configuring your application in the settings.

## Web

### host

The host of your server (often `locahost` or `0.0.0.0`).

### port

The port your server is listening to.

### git [deprecated]

For the production settings, you can set your git remote/branch to identify what is a release.

This is used by the live mode currently to retrieve the last released version and install it locally. We're currently migrating this option to use git tags instead as it may happen you don't have a branch specific for the release (which is not a bad thing).

## Database

### type

The dialect of the database you are connecting to. It can be `postgres`, `mysql` or `sqlite`. Other dialect are intended to see the light in the coming months

e.g. `"type": "postgres"`

### host

The host of the relational database.

`"host": "localhost"`

### port

The port of the relational database.

`"port": 5432`

### database

The name of the database.

`"database": "my-database"`

### username and password

The username and password are used to authenticate the database.

```
...
"username": "postgres"
"password": "my-password"
...
```