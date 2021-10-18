1. Getting started:  
    1. Using Google Cloud Shell (the simplest option):  
        prerequisites: node and npm  
        these are available inside Google Cloud Shell.  
        1. open two separate terminal sessions:  
            * check that your Project Id is shown in yellow/gold in parentheses.
            * in one terminal **cd sample-master/internal**  
            * in the other terminal **cd sample-master/external**  
        1. run **npm install** in each terminal
        1. run **node server.js** in the *internal* terminal
        1. run **npm start** in the *external* terminal
        1. click on the "preview" button of your Cloud Shell.
    1. Alternatively, using Your own machine (Windows users, see note at bottom this file):  
        prerequisites: node and npm  
        1. open two separate terminal sessions:  
            * in one terminal **cd sample-master/internal**  
            * in the other terminal **cd sample-master/external**  
        1. run **npm install** in each terminal
        1. run **node server.js** in the *internal* terminal
        1. run **npm start** in the *external* terminal
        1. Open a browser and navigate to http://localhost:8080

1. The sample app  
Uses nodejs with the express web server on both server and client microservices.  
The internal service receives REST requests on port 8082 and returns mock data.  
The external service unpacks json from the internal service into a html template in the Views folder and returns it to the browser on port 8080.

1. Dependencies  
The internal and external both use the following npm packages:

   * express: a web server  
     * https://www.npmjs.com/package/express  
   * body-parser to convert json and form data in the request into parameters.  
     * https://www.npmjs.com/package/body-parser  
   * mocha, chai and supertest (for unit testing)  
     * https://www.npmjs.com/package/mocha  
     * https://www.npmjs.com/package/chai  
     * https://www.npmjs.com/package/supertest  
   * nyc for code coverage reporting  
     *  https://www.npmjs.com/package/nyc  
     
   The external service uses the following additional libraries:

   * express-handlebars ( a templating library)  
     * https://github.com/ericf/express-handlebars  
   * nock (for mocking the api call)  
     * https://www.npmjs.com/package/nock

1. Windows 
The external/package.json file uses linux-style syntax for environment variables.
Windows users will need to modify the code in order to run the sample locally during development, e.g.
    *     **"start": "set SERVER=http://localhost:8082&& node server.js"**,
    *     **"test": "set SERVER=http://localhost:8082&& nyc mocha"**
