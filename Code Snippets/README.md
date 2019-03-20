# Code Snippets  :

1. **An Object type in Java Script and added functions & variables to it?**

    **Answer**

    **Code**
    ```js
    // Created an Object
    var project = {
    name : "Project Name: Creating an Object Type",
    owner : "Project Owner: Navin",
    description : () => {
            console.log("Project Description: 'project' is a simple object created to add variables and functions for the assignment");
        },
        created : () => {
            console.log("Project Creation: 'project' was created on 18th March 2019");
        }
    };

    console.log(project.name);
    console.log(project.owner);
    project.description();
    project.created();
    ```
    **Console Log**
    ```console
    navinnavi19:~/workspace/Node Learnings $ node app.js 
    Project Name: Creating an Object Type
    Project Owner: Navin
    Project Description: 'project' is a simple object created to add variables and functions for the assignment
    Project Creation: 'project' was created on 18th March 2019
    ```

2. **Create array then add variables and function to it through push()**
    
    **Answer**
    
    **Code**
    ```js
    // Created an Array
    var createArray = [];

    // Created an Object
    var project1 = {
        name : "Project Name: Creating an Object Type",
        owner : "Project Owner: Navin",
        description : () => {
            console.log(project1.name);
            console.log(project1.owner);
            console.log("Project Description: 'project1' is a simple object created to add variables and functions for the assignment");
            project1.created();
        },
        created : () => {
            console.log("Project Creation: 'project' was created on 18th March 2019");
        }
    };

    // Pushing a strings and an Object
    createArray.push("Project1", project1);
    createArray.push("Project2");

    // Creating variables and functions
    var name = "Project2";
    var description = () => console.log("Project Description: 'project2' is a simple array created to add variables and functions for the assignment");

    // Pushing Variables and functions
    createArray.push(name, description);

    console.log(createArray);

    project1.description();
    ```
    **Console Log**
    ```console
    $ node app.js 
    [ 'Project1',
    { name: 'Project Name: Creating an Object Type',
        owner: 'Project Owner: Navin',
        description: [Function: description],
        created: [Function: created] },
    'Project2',
    'Project2',
    [Function: description] ]
    Project Name: Creating an Object Type
    Project Owner: Navin
    Project Description: 'project1' is a simple object created to add variables and functions for the assignment
    Project Creation: 'project' was created on 18th March 2019
    ```

3. **Access the present Working directory**

    **Answer**

    **Code**
    ```js
    console.log(process.cwd());
    ```
    
    **Console Log**
    ```console
     $ node app.js 
    /home/ubuntu/workspace/Node Learnings
    ```

4. **Reads the name of the directory  from the command line arguments and displays the list of directory contents (using fs module)**

    **Answer**

    **Code**
    ```js
    const fs = require('fs');
    const commandLineArg = process.argv[2];

    fs.readdir(commandLineArg, (err, files) => {
        if (err) throw err;
        console.log(`Contents of the ${commandLineArg} folder`);
        files.forEach((file) => {
            console.log(file);
        });
    });
    ```

    **Console Log**
    ```console
    $ node app.js test
    Contents of the test folder
    bar.txt
    foo.html
    foobar.pdf
    ```

5. **Reads the file name from console and displays the contents of the file**
    - Synchronous mode
    - Asynchronous mode

    **Answer**

    **Code**
    ```js
    const fs = require('fs');
    const commandLineArg = process.argv[2];

    // Asynchronous Mode
    fs.readFile(commandLineArg, (err, data) => {
        if(err) throw err;
        console.log("\n Reading the file contents using Asynchronous Method \n");
        console.log(data.toString());
    });

    // Synchronous Mode
    const data = fs.readFileSync(commandLineArg);
    console.log("Reading the file contents using Synchronous Method \n");
    console.log(data.toString());
    ```

    **Console Log**
    ```console
    $ node app.js bar.txt
    Reading the file contents using Synchronous Method 

    Project Name: Creating an Object Type
    Project Owner: Navin

    Reading the file contents using Asynchronous Method 

    Project Name: Creating an Object Type
    Project Owner: Navin
    ```

6. **Displays a message through loop, with delay in between the iterations Using setTimeOut()**

    **Answer**

    **Code**
    ```js
    let maxtime = 1000;

    for(var i = 0; i < 10; i++) {
        let delay = Math.floor((Math.random()*maxtime)+1);
        setTimeout(() => {
            console.log("I am printed at %sms", delay);
        }, delay);
    }
    ```

    **Console Log**
    ```console
    $ node app.js
    I am printed at 88ms
    I am printed at 234ms
    I am printed at 462ms
    I am printed at 510ms
    I am printed at 551ms
    I am printed at 632ms
    I am printed at 651ms
    I am printed at 712ms
    I am printed at 742ms
    I am printed at 837ms
    ```

7. **Using ‘http’ module Downloads the content from google home page to a file**

    **Answer**

    **Code**
    ```js
    const http = require('http');
    const fs = require('fs');

    const options = {
    host: "www.google.com",
    port: "80",
    path: "/"
    };

    const callback = (res) => {
    let body = '';
    res.on('data', (data) => {
        body += data;
    });
    
    res.on('end', () => {
        fs.writeFile('bar.html', body, 'utf-8', (err) => {
        if(err) throw err;
        });
    });
    };

    var req = http.request(options, callback);
    req.end();
    ```

    **Output**

    **Formatted Downloaded Google Homepage**
    
    <p align="center">
    <kbd><img src="https://github.com/NavinNavi19/Node-Basics/blob/master/Code%20Snippets/Images/19-03-2019-7-Google-HomePage-Download.PNG"></kbd>
    </p>

8. **Create a HTTP server that responds to requests. (using http module)**

    **Answer**

    **Code**
    ```js
    const http = require('http');

    const server = http.createServer((req, res) => {
    res.write("<h1>Hello World</h1>");
    res.write("<h2>HTML response from the server</h2>");
    res.write("<p>Created a simple HTTP server that responds to requests with a simple HTML response</p>");
    res.end();
    });

    server.listen(process.env.PORT, process.env.IP)
    ```

    **Output**

    <p align="center">
    <kbd><img src="https://github.com/NavinNavi19/Node-Basics/blob/master/Code%20Snippets/Images/19-03-2019-7-simple-http-server.PNG"></kbd>
    </p>

9. **Chat Application using server and client sockets**

    **Answer**

    **Code**
    ```js
    // getting the TCP library
    const net = require('net');

    // creating sockets array to store the clients sockets that are connecting to the server
    const sockets = [];

    // creating the server to process the client requests from sockets
    var server = net.createServer((socket) => {
        // identify the connecting socket
        socket.name = "Socket" + ' : ' + socket.remotePort ;
        
        // Add this socket to the client array
        sockets.push(socket);
        
        // send a nice welcome message and announce
        socket.write("Welcome " + socket.name + '\n');
        broadcast(socket.name + " joined the server \n", socket.name);
        console.log(socket.name + " joined the server \n");
        
        // handle incoming message from the clients
        socket.on('data', (data) => {
            let message = socket.name + " > " + data;
            broadcast(message, socket.name);
            // log the output to server console
            console.log(message);
        });
        
        // socket connection end event
        socket.on("end", () => {
            let message = socket.name + " left the server \n";
            console.log(message);
            // remove the socket from the socket array
            removeSocket(socket);
            
            // broadcast the end message
            broadcast(message, socket.name);
            
        });
        
        // Handle socket Errors
        socket.on("error", (err) => {
            if (err) console.log("Socket has some problem connecting to the server", err.message);
        });
        
        // Broadcasting the messages
        function broadcast(message, sender) {
            
            // if no socket connected
            if(sockets.length === 0) {
                console.log("Everyone has left the server");
                return;
            }
            
            // Broadcast the message to all the sockets
            sockets.forEach((socket) => {
                // broadcast should not be sent to the same server
                if(socket.name === sender) return;
                socket.write(message);
            });
        }
    });

    // remove the socket from the array
    function removeSocket(socket) {
        sockets.splice(sockets.indexof(socket), 1);
    }

    // Handle server errors
    server.on("error", (err) => {
        if (err) console.log("Server could not start", err.message);
    });

    server.listen(1337, process.env.IP, () => {
        console.log("Server started listening for the socket connections");
    });
    ```

    **Console Log**

    **Client 1**

    ```console
    $ telnet localhost 1337
    Trying ::1...
    Trying 127.0.0.1...
    Connected to localhost.
    Escape character is '^]'.
    Welcome Socket : 54740
    Socket : 54878 joined the server 
    Socket : 54940 joined the server 
    I joined FIRST
    Socket : 54878 > I Joined SECOND
    Socket : 54940 > I Joined THIRD
    ```

    **Client 2**
    
    ```console
    $ telnet localhost 1337
    Trying ::1...
    Trying 127.0.0.1...
    Connected to localhost.
    Escape character is '^]'.
    Welcome Socket : 54878
    Socket : 54940 joined the server 
    Socket : 54740 > I joined FIRST
    I Joined SECOND
    Socket : 54940 > I Joined THIRD
    ```

    **Client 3**
    
    ```console
    $ nc localhost 1337
    Welcome Socket : 54940
    Socket : 54740 > I joined FIRST
    Socket : 54878 > I Joined SECOND
    I Joined THIRD
    ```

    **Server logged everything**
    
    ```console
    $ node server.js 
    Server started listening for the socket connections
    Socket : 54740 joined the server 

    Socket : 54878 joined the server 

    Socket : 54940 joined the server 

    Socket : 54740 > I joined FIRST

    Socket : 54878 > I Joined SECOND

    Socket : 54940 > I Joined THIRD

    Socket : 54740 left the server 

    Socket : 54878 left the server 

    Socket : 54940 left the server 

    Everyone has left the server
    ```

10. **Using ‘mongodb’ module read the data from a table in ‘mongodb’ database and display the details on console.**

    **Answer**

    **Data to be read from the database**
    ```console
    > db.documents.find()
    { "_id" : ObjectId("5c920fb46acbbdb5b39c41d8"), "a" : 1 }
    { "_id" : ObjectId("5c920fba6acbbdb5b39c41d9"), "b" : 2 }
    { "_id" : ObjectId("5c920fc16acbbdb5b39c41da"), "c" : 3 }
    { "_id" : ObjectId("5c920fc86acbbdb5b39c41db"), "d" : 4 }
    ```
    **Node Script to read the data from the database**
    ```js
    const MongoClient = require('mongodb').MongoClient;

    const url = "mongodb://localhost:27017";
    const dbname = "testmongo"

    const client = new MongoClient(url, {useNewUrlParser: true});

    client.connect((err) => {
    if(err) throw err;
    console.log("Connected to the database");
    const db = client.db(dbname);
    readFromDatabase(db, () => {
        client.close();
    });
    });

    function readFromDatabase(db, callback){
    const collections = db.collection("documents");
    collections.find({}).toArray((err, data) => {
        if(err) throw err;
        console.log(data);
    });
    }
    ```

    **Console Log**
    ```console
    [nodemon] starting `node app.js`
    Connected to the database
    [ { _id: 5c920fb46acbbdb5b39c41d8, a: 1 },
    { _id: 5c920fba6acbbdb5b39c41d9, b: 2 },
    { _id: 5c920fc16acbbdb5b39c41da, c: 3 },
    { _id: 5c920fc86acbbdb5b39c41db, d: 4 } ]
    ```
    
11. **Uses ‘mongodb’ module perform ‘CRUD’ operations on a Collection of MongoDB database.**

    **Answer**

    **Code**
    ```js
    const MongoClient = require('mongodb').MongoClient;

    const url = "mongodb://localhost:27017";

    const client = new MongoClient(url, {useNewUrlParser: true});

    const dbname = "testmongo";

    client.connect((err) => {
    if(err) throw err;
    console.log("Connected to the database \n");
    
    const db = client.db(dbname);
    const collection = db.collection('users');
    
    /**
    * C - Create
    * R - Read
    * U - Update
    * D - Delete
    */
    
    collectionCreate(collection, () => {
        collectionRead(collection, () => {
        collectionUpdate(collection, () => {
            collectionDelete(collection, () => {
            client.close();         
            });
        });
        });
    });
    });

    // Create a new collection of objects in the database
    function collectionCreate(collection, callback) {
    let userNames = [
        {user1 : "Flash"},
        {user2 : "Arrow"},
        {user3 : "Access"},
        {user4 : "Speedy"}
    ];
    collection.insertMany(userNames, (err, result) => {
        if(err) throw err;
        if((result.result.n) === 4) {
        console.log("Created a list of 4 users into the collection");
        collectionReadAll(collection);
        callback();
        }
    });
    }

    // Read an object from the "users" collection created in the database
    function collectionRead(collection, callback) {
    collection.find({user1: "Flash"}).toArray((err, data) => {
        if(err) throw err;
        console.log("\nRead a particular data from the collections list");
        console.log(data);
        callback();
    });
    }

    // Update an object with new data into the "users" collection
    function collectionUpdate(collection, callback) {
    collection.updateOne({"user4": "Speedy"}, { $set: {"user4": "Reverse Flash"}}, (err, result) => {
        if(err) console.log(err);
        if(result.result.n === 1) {
        console.log("\nUpdated 4th object with a new data");
        collectionReadAll(collection);
        callback();
        }
    });
    }

    // Delete an object from the "users" collection
    function collectionDelete(collection, callback) {
    collection.deleteOne({"user4": "Reverse Flash"}, (err, result) => {
        if(err) throw(err);
        if(result.result.n === 1) {
        console.log("\nDeleted the 4th object from the collection list");
        collectionReadAll(collection);
        callback();
        }
    });
    }

    // Read all the data from the "users" collection
    function collectionReadAll(collection) {
    collection.find({}).toArray((err, data) => {
        if(err) throw err;
        console.log(data);
    });
    }
    ```

    **Console Log**
    ```console
    [nodemon] starting `node app.js`
    Connected to the database 

    Created a list of 4 users into the collection
    [ { _id: 5c9221be191e2f222f7fa083, user1: 'Flash' },
    { _id: 5c9221be191e2f222f7fa084, user2: 'Arrow' },
    { _id: 5c9221be191e2f222f7fa085, user3: 'Access' },
    { _id: 5c9221be191e2f222f7fa086, user4: 'Speedy' } ]

    Read a particular data from the collections list
    [ { _id: 5c9221be191e2f222f7fa083, user1: 'Flash' } ]

    Updated 4th object with a new data
    [ { _id: 5c9221be191e2f222f7fa083, user1: 'Flash' },
    { _id: 5c9221be191e2f222f7fa084, user2: 'Arrow' },
    { _id: 5c9221be191e2f222f7fa085, user3: 'Access' },
    { _id: 5c9221be191e2f222f7fa086, user4: 'Reverse Flash' } ]

    Deleted the 4th object from the collection list
    [ { _id: 5c9221be191e2f222f7fa083, user1: 'Flash' },
    { _id: 5c9221be191e2f222f7fa084, user2: 'Arrow' },
    { _id: 5c9221be191e2f222f7fa085, user3: 'Access' } ]
    ```


<!--
**Answer**

**Node Script**
```js
```

**Console Log**
```console
```
-->
