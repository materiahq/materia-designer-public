# Serving static content

Your API can host multiple endpoint, but you often need to also send static content through your API.

There is a special folder for that in your application directory. You can create a `web/` folder and put all the static content you need (e.g. html files, javascript files, css files, images, videos, gif etc...).

By default, if the file `web/index.html` exists, it assume it's your root file for your front-end (`/` endpoint)

![todo web](/img/gif/todo-website.gif)

# Table of routing

In this table, we assume you're hosting Materia server on localhost:8080.

URL                                                  | response
-----------------------------------------------------|---------------
http://localhost:8080/                               | web/index.html
http://localhost:8080/css/main.css                   | web/css/main.css
http://localhost:8080/file-that-not-exists           | web/404.html
http://localhost:8080/api/test                       | execute endpoint test
http://localhost:8080/api/endpoint-that-doesnt-exist | return 404 error in json

#### Next step: [Deploying your application](/docs/guide/deploy)