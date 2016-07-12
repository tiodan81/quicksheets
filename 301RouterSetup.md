# Starting a New Project with NPM & Page.js

To create a Single Page App project using `page.js` for routing, you need to install `page.js` and `express`. 

`Page.js` handles client-side routing by triggering callback functions when a route change happens. `Express` lets `page.js` work by ensuring that route changes don't trigger HTTP requests.

## Installing page.js

Copy the source code from the `vendor/scripts/page.js` file in the class blog and link to that file with a `<script>` tag in the body of `index.html`

**OR**

Include a `<script>` in `index.html` that links to a CDN

## Installing express

In your terminal, navigate to the root of your project and do:

```
$ npm init
```

`npm init` will prompt you to answer some basic questions about the project and create a `package.json` file. That file will track your answers and keep a list of any dependencies for your project. If you are content with the default answers, you can run `npm init -y` (meaning, say 'yes' to all the questions). You can always edit them later in `package.json`.

Once you have initialized NPM, install express as a dependency with the terminal command

```
$ npm install --save express
```

Now `package.json` should show 

```json
"dependencies": {
    "express": "^4.13.3"
  }
```

*note:* the version number might not match `^4.13.3` because NPM will install the latest stable version of express.

## Setting up the server

Copy `server.js` from the blog starter code to the root directory of your project. This file will ensure that no matter which route the user requests, `index.html` will still be shown.

Make sure that `package.json` contains the line: 

```json
"main": "server.js"
```

If you are **not** using the GitHub API, remove the following references to `express-request-proxy` from `server.js`:

```javascript
var requestProxy = require('express-request-proxy')

...

var proxyGitHub = function(request, response) {
  console.log('Routing GitHub request for', request.params[0]);
  (requestProxy({
    url: 'https://api.github.com/' + request.params[0],
    headers: { Authorization: 'token ' + process.env.GITHUB_TOKEN }
  }))(request, response);
};

app.get('/github/*', proxyGitHub);
```

## Using the GitHub API

If your app will use the GitHub API, you should also include the `express-request-proxy` package. This lets you ensure that `server.js` will use your GitHub token any time a request is made to GitHub. Do:

```
$ npm install --save express-request-proxy
```

## Final steps

1. Create a `routes.js` file where you will specify the callback functions `page.js` should use to handle routing
2. Before you git A-C-P these changes, be sure to put the `node_modules` directory in your `.gitignore` file. There's no need to track those vendor files in git or send them to GitHub since they are all listed in `package.json`