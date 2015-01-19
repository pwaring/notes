# Node.js

`npm install -g grunt-cli`: `-g` means 'install globally'. Generally utilities should be installed globally, whereas app-specific packages should not.

`npm init`: Generates a `package.json` file to get you started.

npm will complain unless `package.json` has a repository URL and a non-empty `README.md` file is included.

npm packages that a project relies on can be found in the `node_modules` directory (which should be added to your `.gitignore` file).

## Express

 * Express defaults to a status code of 200, this does not have to be specified explicitly.
 * The order in which routes and middleware are added/specified matters - first match wins. Do not put 404 handlers as the first route.
