# Hello World

Simple *Hello World* to create a node.js project that uses the `deployr`
JavaScript Client Library and executes the repository-managed R script 
`DeployR - Hello World.R` on an anonymous project passing in `R numeric` value 
of '10' named 'input_randNum'.


Install
=======

1. `$git clone https://github.com/swells/hello-world.git`

2. `$ cd hello-world`

3.  `$ npm install`

4. Set the proper deployr server endpoint in `index.js`

```
deployr.configure({ host: 'http;//localhost:7300' });
```

Run
===

- `$node index.js`


Steps on how sample was created from scratch
============================================


- [download and install](http://nodejs.org/download/) Node.js

- ```$ mkdir hello-world ```

- ```$ cd hello-world ```

- ```$ npm init```

  This builds your `package.json` asking you some questions. You can modify
  this file by hand later as well. One of the questions asked is what your
  _main_ should be called. I choose `index.js` and it was created for us.

- ```$ npm install deployr -save```

  This will pull in `deployr` as a dependency and the `-save` with update
  your `package.json` indicating that `deployr` is a runtime dependency on the
  `hello-world` project.

- Build your `hello-world` project/app by editing `index.js`:


```js

#!/usr/bin/env node

var deployr = require('deployr');

// ============================================================================
// Set the DeployR server endpoint URL
// ============================================================================

deployr.configure({ host: 'http;//localhost:7300' });

//
// Execute R script `/author/directory/filename`
// - author:    testuser
// - directory: root
// - filename:  DeployR - Hello World.R
//
deployr.script('/testuser/root/DeployR - Hello World.R')
    .numeric('input_randomNum', 10)
    .error(function(err) {
        // error
    })
    .end(function(res) {
       // success
    });

```
