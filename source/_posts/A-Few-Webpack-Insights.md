---
title: A Few Webpack Insights
date:   2018-06-25 17:03:27 -0700
tags: webpack
---

Webpack has always been a little mysterious for me, which is why I've tended to fall back to Create-React-App. A couple of insights that I received today that I wanted to pass along:

````
 "scripts": {
    "start": "node src/server/index.js",
    "build": "webpack --mode production",
    "client": "webpack-dev-server --mode development --devtool inline-source-map --hot",
    "server": "nodemon src/server/index.js",
    "dev": "concurrently \"npm run server\" \"npm run client\""
  }
````

This was the scripts that I built into my package.json for a back-end express server and a front-end react rendering. What I want to point out are these (for me) interesting insights that helped take away the mysteriousness of webpack machinations:

- the 'start' script will be used by the app after production has been invoked, and that's because all the html, css, and js files will have been bundled by webpack into a file called 'bundle.js' which is sitting in a folder called "dist". 
- the 'build' script uses a [**mode**](https://webpack.js.org/concepts/mode/) that webpack offers, and it has to do optimizations. For production, it offers these:

````
Provides process.env.NODE_ENV with value production. Enables FlagDependencyUsagePlugin, FlagIncludedChunksPlugin, ModuleConcatenationPlugin, NoEmitOnErrorsPlugin, OccurrenceOrderPlugin, SideEffectsFlagPlugin and UglifyJsPlugin.
````

- the 'client' script spins up [webpack-dev-server](https://webpack.js.org/configuration/dev-server/) which does what nodemon does, refreshing browser changes instead of back-end server. Once again we have that **mode** for optimizations, we have a [source map](https://webpack.js.org/guides/development/#using-source-maps) which is good for development and we've set it for **hot** reloading

- the 'server' script is for spinning up the express server
- finally, 'dev' script allows us to access the html, css, js files without webpack bundling them

Anyways, diving into studying these parts of webpack were helpful for me!
