# Hands on assignments  :

1. **Create an Object type in Java Script and add functions & variables to it?**

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

2. **Create an array, add variables and function to it through push()**
    
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

3. **Create a ‘js’ file with code that provides implementation for ‘pwd’ command from ‘Node’ shell.**

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

4. **Create NodeJS based script file, that reads the name of the directory  from the command line arguments and displays the list of directory contents (using fs module)**

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

5. **Create a Node JS script that reads the file name from console and displays the contents of the file**
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

6. **Create a Node JS Script that displays a message through loop, with delay in between the iterations Using setTimeOut()**

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

7. **Create a Node JS Script, using ‘http’ module that downloads the content from a web page to a file**
    - E.g. to download the google home page

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
    <kbd><img src="Code%20Snippets/Images/19-03-2019-7-Google-HomePage-Download.PNG"></kbd>
    </p>

8. **Create a simple HTTP server that responds to requests with a simple HTML response. (using http module)**

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
    <kbd><img src="Code%20Snippets/Images/19-03-2019-7-simple-http-server.PNG"></kbd>
    </p>

9. **Create a program to accept client requests on a socket (using net module) and further to create client socket for communication**
    - Create Server socket that listens at a port number and creates sockets for every client request.
    - Send a message from any of the client (socket) and through code the message should be propagated to all the sockets which are active
    - Test it through ‘telnet’, to see the message echo.

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

10. **Create a Node JS script that uses ‘mongodb’ module to read the data from a table in ‘mongodb’ database and display the details on console.**

    **Answer**

    **Code**
    ```js
    ```

    **Console Log**
    ```console
    ```
    
11. **Create a Node JS Script that uses ‘mongodb’ specific modules and provides ‘CRUD’ operations on a Collection of MongoDB database.**

    **Answer**

    **Code**
    ```js
    ```

    **Console Log**
    ```console
    ```


<!--
**Answer**

**Code**
```js
```

**Console Log**
```console
```
-->
