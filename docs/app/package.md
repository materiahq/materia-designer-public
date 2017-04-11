package.json
============

The `package.json` file contains the basic informations about your application - name, version, dependencies (containing Materia Addons) and basic information for Materia Designer.

It should look something like:

```json
{
  "name": "app-name",
  "version": "0.1.0",
  "description": "App Description",
  "main": "index.js",
  "scripts": {
    "start": "materia start",
	"prod": "materia start --mode=prod"
  },
  "author": "Your Team",
  "license": "MIT",
  "dependencies": {
    "materia-server": "^0.7.0"
  },
  "materia": {
	"display_name": "App Name",
    "icon": {
      "color": "blue-400"
    }
  },
  "engines": {
    "node": ">=7.7.3"
  }
}
```

## name

The name of the application

## materia

Used by Materia Designer to display your application.

Currently, only **color** and the **display_name** are available and support all [Material colors](https://material.google.com/style/color.html#color-color-palette).

## addons

Addons are NPM dependencies. When your start Materia Server it will check your dependencies and check which dependencies is a Materia Addon by looking their package.json and check if there is a non null `materia` key inside.

e.g. you can install the User Management addon using this command `yarn add @materia/users` in your application folder.