Now let's add a more realistic Node.js application.

## Task

### Clone the Project

In your working terminal, clone the repository (project);

```git clone http://git.itworx.cloud/<username>/project-atomic.git .```{{execute}}

### Populate Project

Create a new `package.json`{{open}} and the below content;

<pre class="file" data-filename="./package.json" data-target="replace">
{
  "name": "project-atomic",
  "version": "1.0.0",
  "description": "Project Atomic",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "http://git.itworx.cloud/aossama/project-atomic.git"
  },
  "author": "",
  "license": "Apache License",
  "dependencies": {
    "express": "^4.16.3"
  }
}
</pre>

Create another file called `app.js`{{open}} with the below content;

<pre class="file" data-filename="./app.js" data-target="replace">
const express = require('express')
const app = express()

app.get('/', (req, res) => res.send('Hello World!'))

app.listen(3000, () => console.log('Example app listening on port 3000!'))
</pre>

And add the `.gitignore`{{open}} file with the below content;

<pre class="file" data-filename="./.gitignore" data-target="replace">
node_modules/
</pre>

### Save Changes and Push

Add, commit and push the modified content;

```git add app.js package.json .gitignore```{{execute}}

```git commit -m "Add skeleton application"```{{execute}}

```git push```{{execute}}
