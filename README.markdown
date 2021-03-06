README bower.plugin
===================

1. Install all the dependencies using `bower install`
2. If you need to add new libraries/dependencies (lib/dep) to the project,
   add in browser.json and run bower install. Voila, 
   you`ll get access to that lib/dep

Example:

        /* browser.json */
        {
          "name": "test-app",
          "version": "0.0.1",

          // Requires JS, config settings defined in browser.json
          "app": {
            "baseUrl": "/assets/js", // Define app assets directory
            "start": ["app"], // Define app start file
            "paths": {
              "jquery": "/browser_modules/jquery/index"
            }
          },

          // can be accessed directly via requirejs
          "dependencies": {
            "jquery" : "*",
            "underscore" : "*",
            "backbone": "*"
          }
        }

        /* assets/js/app.js */
        define('app', 
          ['require', 
           'jquery', 
           'underscore', 
           'backbone'], function ( require ) {
          // Loaded ! Booyah !
        });

        /* index.html */
        <script data-main='bower' src='require.js'></script>

About the plugin
================
Simple glue plugin to automatically expose lib/deps added in browser.json
to the requirejs framework to be used.


TODO
====
1. r.js build script to utilize the same mechanism.
2. Better way of figuring out library/script dependencies with each other
perhaps merge all `browser.json` from all the scripts and add them as libraries
for require js config