Starting/stopping the server
============================

You can always see if the server is running on the left with the green/red dot.

![stop start server](/img/gif/stop-start-server.gif)

Behind the scene, Materia Designer is using Materia Server in dev mode to host your API.

In the settings of Materia, you can change the port of the server if you need it.

![app settings](/img/settings.png)

Using Materia Server
====================

You can run your application on any server using the Materia Server CLI:

```sh
$> materia start
```

![server start stop cli](/img/gif/stop-start-server-cli.gif)

It will run the server in dev mode (using the development configuration). To run it for production, use `--mode=prod`:

```sh
$> materia start --mode=prod
```

In the `server.json` file, you have a configuration for the development, and a configuration for the production as they always differ in some ways.

#### Next step: [Structuring data](/docs/guide/structure-data)