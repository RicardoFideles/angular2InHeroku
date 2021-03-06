# How to publish a angular 2 app in Heroku

heroku create

### Add a new script in package.json

```
"scripts": {
  // ...
  "postinstall": "ng build --aot -prod"
}
```

### Change the dependencies of angular cli from devDepencies to dependencies

```
"dependencies": {
  // ...
  "@angular/compiler-cli": "2.2.3",
  "angular-cli": "1.0.0-beta.22-1",
}
```

### Change the start script

```
"scripts": {
  // ...
  "start": "node server.js"
}
```


### Add engines

```
"engines": {
  "node": "6.9.2",
  "npm": "3.10.9"
}
```

### Instal express

npm install --save express

### create a file `server.js`

```
// server.js
const express = require('express');
const app = express();
// Run the app by serving the static files
// in the dist directory
app.use(express.static(__dirname + '/dist'));
// Start the app by listening on the default
// Heroku port
app.listen(process.env.PORT || 8080);

```

### Push to Heroku

```
git add .
git commit -m "first deploy"
git push heroku master

```