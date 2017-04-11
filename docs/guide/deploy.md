Deploying your application
==========================

The deployment is something we're working on actively. Currently, there is no automatic way of deployment (WIP).

So, to deploy your application, we advice to proceed the same way you do than a Node.js application (as Materia behind the scene is just a Node.js application).

You can use ssh or other methods to send your application source code on your server and then you can use [Materia Server](http://npmjs.com/package/materia-server) to start the an application in production mode using: `materia start --mode=prod`

To start Materia Server in production mode, you need to configure the production server settings and the production database settings to determine how your application should be started. It can be done on Materia Designer in your application settings.

Remember that the production settings (database/server) are viewed from the server, so for instance, the host is often `localhost` or `0.0.0.0` and not the external IP.