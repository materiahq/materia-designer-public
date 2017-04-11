Structuring data
================

Structuring data is the key to every good application. To structure well your data, you first need to visualize it properly. To do this, go in the **Entities** menu.

![Structure data](/img/screen-entities.png)

The main panel is an overview of your entities, the fields inside an entity, and the relations between entities. Directly within Materia, you can create your architecture to match your needs.

**Materia is synchronized with your database. When you do an operation in Materia designer, changes will be replicated on your database. When you start an application on Materia Designer, it will get the schema of the database to check if the models differ in some ways with it (cf: [Synchronizing with your database](/docs/guide/synchronize-db) chapter)**

Entity
------

An entity is the representation of your table in your database. It has a set of fields and a set of relation.

For the beginner, you can see an entity as an excel table with each fields as a column. You can then fill your excel row by row. The difference is you can have lots of excel table, these excel tables can be linked between them, and you can make query to retrieve exactly the data you need.

Each entity is stored in its corresponding json file in the `entities/` folder.

![Todo entity](/img/gif/todo-entities.gif)

Field
-----

A field is a feature of an entity (e.g. field **name** of the entity **user**). A field is typed: this mean you need to specify if the data in this field will be an integer, a text or a boolean.

A field is defined by a name and can have multiple properties to have exactly the behavior you're expecting.

![Field settings](/img/field-settings.png)

**Field type**

The data inside the database is typed. This mean you have to say if what you're storing here.

The type available are:

* **Text** (any text e.g. "team@getmateria.com")
* **Number** (number only e.g. 42)
* **Boolean** (true/false value)
* **Float** (float numbers e.g. 42.42)

We're looking to add more high level type as "Image" or "File" in a near future.

**Required field**

A Field can be required, that mean you can't create data with this field set to `NULL` (blank value).
This property is used for mandatory data as the email and password in a user account.

**Primary key**

The primary key is the unique field to differentiate a row with another. In most case, the primary key is a field named **id** with the type **number** and the **auto increment** property enabled.

Each entity need to have a field with the property primary key enabled.

**Unique field**

A field can be unique (e.g. the email of a user is unique (and it's maybe not the primary key)). If you try to create 2 same entries in your entity which contains a field unique will trigger an error.

**Default value**

A field can have a default value (e.g. the field **genre** can be **male** or **female** with **male** as default value)

**Auto increment**

A field as primary key can also have the property auto increment which mean that this field don't have to be filled at the creation of an entry. It will automatically increment an id (first entry has 1, 2nd entry has 2, 3rd entry has 3 etc...)

Relation
--------

To illustrate this chapter we'll take the example of a SAAS todo application. 

* We want a **User** to be able to write multiple **Todo** associated with his account. A **Todo** is written by only one **User** => One to many
* We want a **Todo** To be able to have multiple **Tags** associated with its task. A **Tags** can be used by multiple **Todo** => Many to many

You can set relations to link 2 entities. In Materia, you have 2 types of relation:

* **One to many - BelongsTo** - The relation between **Todo** and **User**
* **Many to many - BelongsToMany** - The relation between **Todo** and **Tags**

In Materia Designer, you can see the relations between entities by a line which link them.

**BelongsTo**

To create a belongsTo relation, you just need to tell Materia designer the way of the relation and the name of the reference. The reference is a field stored in the "child" entity (in our example the **Todo** entity).

![belongsTo](/img/gif/relations-belongsTo.gif)

**BelongsToMany**

To create a belongsToMany relation, Materia create for you a relation table to store the associations data.

In our Todo example, it mean it will store the id of the todo and the id of the tag in this association when a todo has this tag.

![belongsToMany](/img/gif/relations-belongsToMany.gif)

#### Next step: [Synchronizing with your database](/docs/guide/synchronize-db)