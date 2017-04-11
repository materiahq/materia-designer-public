You can automate some tasks by creating an addon. An addon can automatically create some entities / queries / endpoints and create new permissions for your endpoints. An addon can have its own custom view to let developers configure your addon.

A marketplace of addons is in the roadmap and should be soon available.

# How an addon is architectured

An addon is a Materia application with an `index.js` file which is used to bootstrap your addon.

An existing Materia application can be easily converted into an addon:

* Copy - paste your application folder in the node-modules folder
* Add the folder name of your addon in the `package.json` as dependencies

** => Materia should now recognize your addon and load/sync it properly with your existing structure. **

An addon can be extended by updating its entity's relations/fields.

To install existing addons, you can run the following command: `materia addons install {addon_name}`

e.g. `materia addons install @materia/user-management`

The goal of an addon is to deliver a generic feature which can be reused in multiple application. 


Examples of what can be done with an addon:

* Addon 'simple-login': Authenticate your user.
	* It would add all endpoints for signin / logout / lost password
	* It would add permissions for logged users
	* It would have a custom view to configure OAuth (Facebook / Twitter / Google connect) and to see the list of your signed up users.

* Addon 'payment': Easy payment solution with Stripe
	* It would add relations with your user entity to handle payment
	* it would add endpoints to add the signed-up user to a plan
	* It would add permissions for paying users
	* It would have a custom view to configure your plan / pricing table and to see the list of your customers / display a chart of income.

* Addon 'admin': Create an admin dashboard to manage your data
	* It would add some file in your `web/` folder
	* It would have a custom view to configure the authentication (admin password or specify the admin users from your `user` entity).

* Addon 'chartify': Create simple charts from your entities
	* It would have a custom view to configure what chart you want to display and to display the chart.

etc.

We are working hard on this part to bring these addons in the next big release.

