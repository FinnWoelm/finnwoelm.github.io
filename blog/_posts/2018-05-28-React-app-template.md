---
layout: post
title:  "React App Template"
date:   2018-05-28
categories: react
excerpt: "5 steps to get started with React, Material Design, and Hot Reloading."
---

If you're new to React, you may be wondering how to get yourself started. Below
are the five steps I follow to set up any new React app that I start working on.

# Step 1: Create new React app

Let's get started by creating a new react project using [`create-react-app`](https://github.com/facebook/create-react-app):

``` shell
$ npx create-react-app "name-of-app"
```

# Step 2: Set up Material CSS framework

We will install and use [`material-ui`](https://material-ui.com/).

``` shell
$ yarn add @material-ui/core
```

You can now use Material components in your app, like so:

~~~ javascript
// some-file.js
// import button
import Button from '@material-ui/core/Button';

// use Button
function MyComponent(props) {
  return (
    <Button>
      Click me
    </Button>
  );
}
~~~

# Step 3: Set up Roboto font

1. We will install and use [`typeface-roboto`](https://github.com/KyleAMathews/typefaces/tree/master/packages/roboto).

   ``` shell
   $ yarn add typeface-roboto
   ```

2. Require typeface roboto in `src/index.js`:

   ``` javascript
   // src/index.js
   import React from 'react';
   ...

   // load Roboto font
   require('typeface-roboto');

   ReactDOM.render(...);
   ...
   ```


# Step 4: Set up Material icons

We will install and use [`material-ui/icons`](https://www.npmjs.com/package/@material-ui/icons).

``` shell
$ yarn add @material-ui/icons
```

You can now use Material icons in your app, like so:

~~~ javascript
// some-file.js
// import icon
import AddIcon from '@material-ui/icons/Add';

// use icon
function MyComponent(props) {
  return (
    <AddIcon />
  );
}
~~~


# Step 5: Set up hot reloading
Credit for [hot reloading without ejecting Create React App belongs to Dave Ceddia](https://daveceddia.com/hot-reloading-create-react-app/).

1. Add react-app-rewired, react-app-rewire-hot-loader, and react-hot-loader packages:

   ~~~ shell
   $ yarn add react-app-rewired react-app-rewire-hot-loader react-hot-loader
   ~~~

2. Create `config-overrides.js` in the root directory (not the `src` directory) and add the following code:

   ~~~ javascript
   // config-overrides.js
   const rewireReactHotLoader = require('react-app-rewire-hot-loader');

   module.exports = function override(config, env) {
     config = rewireReactHotLoader(config, env);
     return config;
   }
   ~~~

3. Set up hot reloading in `src/index.js`:

   ~~~ javascript
   // src/index.js
   import React from 'react';
   import ReactDOM from 'react-dom';
   ...
   import { AppContainer } from 'react-hot-loader';

   // The call to render must be wrapped in a function:
   const render = Component => {
     ReactDOM.render(
       // Wrap App inside AppContainer
       <AppContainer>
         <App />
       </AppContainer>,
       document.getElementById('root')
     );
   };

   // Register Service Worker
   registerServiceWorker();

   // Render app once
   render(App);

   // Webpack Hot Module Replacement API
   // Replace ./App below with path to App.js
   if (module.hot) {
     module.hot.accept('./App', () => {
       render(App);
     });
   }
   ~~~

4. Change scripts in `package.json` to use `react-app-wired` instead of `react-scripts`:

   ~~~ json
   "scripts": {
     "start": "react-app-rewired start",
     "build": "react-app-rewired build",
     "test":  "react-app-rewired test --env=jsdom",
     "eject": "react-scripts eject"
   }
   ~~~
