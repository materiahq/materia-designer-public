When a endpoint is called, it first check that the user that make the call has the good permission to execute the query.

When you've just installed Materia designer, there is no permission defined. A permission can only be defined by an addon.

e.g. An addon of user management would add a permission like `isConnected`. An addon of payment would add a permission like `isPayingUser`.

When you're creating an endpoint, you can define which permission should be checked.

By default, there is no permission that means everybody can access your endpoint.
