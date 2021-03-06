To run index.js, Express.js and Node.js should be installed in the path.  If you run the code on localhost, the address should be "localhost:3000". If you run it on the server, the address should be "http://3.93.183.130:3000/". 

The steps in this README.md works for both server and localhost. However, while there is no other requirements for localhost to run the code, you need to get access to the server to make the code run there. For how to connect to the server, please refer to the private document 'Server Manipulation'. In most cases, code running on localhost is for testing. On your terminal, on the path of the package, 

Install NVM 
    
    $ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
    
Install Node.js
    
    
    $ nvm install <latest version number>
    e.g. $ nvm install 11
    
Install Express.js


    $ npm init
    $ npm install express --save-dev
    $ npm install body-parser --save
Just use the default settings when installing and use $ ls to check if you have node_modules directory and package.json after you install

Install rethinkdb


    $ npm install rethinkdb
Run code


    $node index.js

Once you have already set and installed the environment, you just need the last step to run the code. Note that right now the code is executing, but you cannot quit to keep the server continuing listening. Therefore, we need to make the program run in background. 

Press Ctrl+Z to suspend the job. It will return something like 
    
    [1]+  Stopped                 node index.js 
Then just let the job run in background. 
    
    
    $bg %1
Note the number following the percentage should match the number given back by Ctrl+Z (the number in bracket above). 

Besides, you may also wanted to change the code in index.js and make it re-run on the server. To do this, we need to first kill the previous job that is currently listening on port 3000 or 3001, depending on which api we wanted to edit. 

Find such job
    
    
    $lsof -i:3000
    or
    $lsof -i:3001

This will return all jobs that are listening on port indicated with their PID. 

Kill the job
    
    
    $kill PID

Replace 'PID' with the PID related to the job. 
Then, you can edit the index.js file. 

    $nano index.js

It will lead you to an editor where you can edit your code. Once the revisions are completed, just re-run the code.

    $node index.js

The only thing left is to repeat the step to make the program run in background. 

When it is time for testing the API, just open software 'Postman' or any other software that can send http requests and receive responses to test. For the use of API, please refer to the 'Weatherwayz API Documentation'. 
