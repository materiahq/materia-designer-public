entities/*.json
===============

The json files in the `entities/` folder contains the informations (models) about your entities.

```json
{
	"id": "cc34f8b5-c1e3-472e-b764-9d19c154dede",
	"fields": [
		{
			"name": "id_myentity",
			"type": "number",
			"primary": true,
			"unique": true,
			"required": true,
			"read": true,
			"write": true,
			"default": false,
			"autoIncrement": true
		},
		...
	],
	"relations": [
		{
			"type": "belongsTo",
			"field": "id_owner",
			"reference": {
				"entity": "mymaster",
				"field": "id_mymaster"
			}
		},
		...
	],
	"queries": [
		{
			"id": "listFiltered",
			"type": "findAll",
			"params": [],
			"opts": {
				"conditions": [
					{
						"name": "myfiltered_field",
						"operator": "=",
						"value": "myvalue"
					}
				]
			}
		},
		...
	]
```

---

The filename gives the entity name.

### id

A unique identifier to allow renaming without loss. This should be unique and not modified once the entity created.

`"id": "cc34f8b5-c1e3-472e-b764-9d19c154dede"`

### fields

An array describing the fields in the entity

A field contains several properties:

 - **name**: The field's name
 - **type**: Type of the field's value. Can be `text`, `number`, `date`, `boolean` or `float`.
 - **primary**: Set to `true` if this field is part of the primary key
 - **unique**: Set to `true` if this field is unique, or any string if part of a unique group.
 - **required**: Set to `true` if this field is required and cannot be nullable.
 - **autoIncrement**: When creating the table in database, its primary key will be increased when adding new rows.
 - **default**: Set to any default value if you want the field to be filled at the creation of a row.
 - **read**: If set to `true`, its value will be sent in default queries.
 - **write**: If set to `true`, this field can be updated by default queries.


### relations

An array describing the relations with the other entities

A relation contains several properties:

 - **type**: `belongsTo`, `hasMany`, or `belongsToMany`. This correspond to relations 1-n, n-1, n-n in a relational database.
 - **field**: Field used to link the other entity. This required for `belongsTo` relations and not used for `hasMany` relations.
 - **as**: When using a `belongsToMany` relation, this is the name of the field linked to the entity in the through table.

 - **reference.entity**: Name of the target entity of the relation
 - **reference.field**: Name of the target field, depending the relation type
 - **reference.as**: For `belongsToMany` relations, the name of the field in the through table linked to the target entity.

### queries

An array containing the queries of the entities.

 - **id**: Name of the query
 - **type**: Possible values: `findAll`, `findOne`, `create`, `update`, `delete`, `sql`, `custom`
 - **params**: Array of paramaters (c.f. below)

 - **opts.conditions**: Array of conditions (c.f. below), not used with type `sql`, `custom`.
 - **opts.query**: The sql query when using type `sql`
 - **opts.file**: The file path relative to the materia's app folder. Only used with type `custom`

A parameter has a `name`, `type` and `required` fields:

 - **name**: Name of the parameter
 - **type**: Type of the param value. Can be `text`, `number`, `date`, `boolean` or `float`.
 - **required**: Set to `true` if this is a required param.


A condition has a `name`, `operator`, `value`, and `operand` field:

 - **name**: Field's name where the condition is applied.
 - **operator**: Possible values: `=`, `!=`, `<`, `>`, `>=`, `<=`, `like`, `not like`, `ilike`, `not ilike`
 - **value**: The value to use in the operation. If set to a string beginning with `=`, the parameter with the following name will be used.
