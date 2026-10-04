# Node.js Basics, Modules and Libraries

Node.js is an open-source JavaScript runtime environment that allows JavaScript to run outside a web browser.

It is mainly used to develop server-side and backend applications.

Node.js can be used to create web servers, handle client requests, work with files, and build APIs.


## 1. Basic Node.js Commands

### `node -v`

Displays the installed Node.js version.

``` bash
node -v
```

### `npm -v`

Displays the installed npm (Node Package Manager) version.

``` bash
npm -v
```

### `npm init`

Initializes a Node.js project and creates a `package.json` file.

``` bash
npm init
```

### `nodemon`

Nodemon automatically restarts a Node.js application whenever changes
are made to the source code.

``` bash
nodemon filename.js
```

------------------------------------------------------------------------

# 2. Modules in Node.js

A **module** is a reusable block of code containing related functions,
variables, or objects. Modules help divide a program into smaller,
manageable and reusable files.

## Types of Modules

1.  **Built-in modules** -- provided by Node.js, such as `os`, `http`,
    and `fs`.
2.  **User-defined modules** -- modules created by the programmer.
3.  **Third-party modules/packages** -- installed using npm.

## Importing a Module with `require()`

``` js
const variableName = require("module_name");
```

Example:

``` js
const os = require("os");
```

For a local/user-defined module:

``` js
const math = require("./math");
```

## Exporting Multiple Functions

Suppose `math.js` contains:

``` js
function add(a, b) {
    return a + b;
}

function sub(a, b) {
    return a - b;
}

module.exports = {
    add,
    sub
};
```

Import both functions using object destructuring:

``` js
const { add, sub } = require("./math");

console.log(add(10, 5));
console.log(sub(10, 5));
```

Functions can also be exported individually:

``` js
exports.add = (a, b) => a + b;
exports.sub = (a, b) => a - b;
```

### `module.exports` and `exports`

-   `module.exports` can export a function, object, variable, or
    multiple values together.
-   `exports.name` is a convenient way to add individual
    properties/functions to the exported object.

------------------------------------------------------------------------

# 3. Libraries / Built-in Modules

In Node.js, functionality such as operating-system information, HTTP
servers, and file handling is provided through built-in modules. In
these notes, the important built-in modules are **OS**, **HTTP**, and
**File System (fs)**.

------------------------------------------------------------------------

# 4. OS Module

The **OS module** provides information related to the operating system.

``` js
const os = require("os");
```

## Methods Used / Discussed in the OS Module

  Method            Purpose
  ----------------- ------------------------------------------------
  `os.freemem()`    Returns available/free system memory in bytes.
  `os.totalmem()`   Returns total system memory in bytes.
  `os.platform()`   Returns the operating-system platform.
  `os.hostname()`   Returns the computer's hostname.
  `os.homedir()`    Returns the current user's home directory.

Example:

``` js
const os = require("os");

console.log("Free Memory:", os.freemem());
console.log("Total Memory:", os.totalmem());
console.log("Platform:", os.platform());
console.log("Hostname:", os.hostname());
console.log("Home Directory:", os.homedir());
```

> From the originally taught code, the main OS method used is
> `os.freemem()`.

------------------------------------------------------------------------

# 5. HTTP Module

The **HTTP module** is used to create an HTTP/web server and handle
client requests and server responses.

``` js
const http = require("http");
```

## Methods / Properties Used in HTTP

  -----------------------------------------------------------------------
  Method / Property                   Purpose
  ----------------------------------- -----------------------------------
  `http.createServer()`               Creates an HTTP server.

  `server.listen()`                   Starts the server and makes it
                                      listen on a specified port.

  `res.end()`                         Sends the response and ends it.

  `req.url`                           Gives the URL/path requested by the
                                      client.

  `req.headers`                       Gives the headers received with the
                                      request.
  -----------------------------------------------------------------------

## Creating a Basic HTTP Server

``` js
const http = require("http");

const myServer = http.createServer((req, res) => {
    console.log("Request received");
    res.end("Hello from Server!");
});

myServer.listen(8000, () => {
    console.log("Server is Started");
});
```

### Request and Response

The callback passed to `createServer()` is the **request handler
function**.

``` js
(req, res) => { }
```

-   `req` represents the incoming request.
-   `res` is used to send the response back to the client.

### Accessing Request Headers

``` js
console.log(req.headers);
```

### Accessing Requested URL

``` js
console.log(req.url);
```

------------------------------------------------------------------------

# 6. File System (`fs`) Module

The **File System module** is used to work with files.

``` js
const fs = require("fs");
```

## Method Used in the `fs` Module

  -----------------------------------------------------------------------
  Method                              Purpose
  ----------------------------------- -----------------------------------
  `fs.appendFile()`                   Appends data to the end of a file.
                                      It can be used to maintain a log
                                      file.

  -----------------------------------------------------------------------

Example:

``` js
const fs = require("fs");

const log = `${Date.now()}: New Request received`;

fs.appendFile("log.txt", log + "\n", (err) => {
    if (err) {
        console.log("Error in writing to file");
    }
});
```

`Date.now()` is a JavaScript method used here to obtain the current
timestamp for the log entry.

------------------------------------------------------------------------

# 7. HTTP Server with Request Logging

The HTTP and File System modules can be used together to create a server
and maintain a request log.

``` js
const http = require("http");
const fs = require("fs");

const myServer = http.createServer((req, res) => {
    const log = `${Date.now()}: New Request received`;

    fs.appendFile("log.txt", log + "\n", (err) => {
        if (err) {
            console.log("Error in writing to file");
        }

        res.end("Hello from Server!");
    });

    console.log(req.headers);
});

myServer.listen(8000, () => {
    console.log("Server is Started");
});
```

------------------------------------------------------------------------

# 8. Routing Using `req.url`

**Routing** means deciding which response should be sent according to
the requested URL.

  Requested URL   Response
  --------------- --------------------
  `/`             Homepage
  `/about`        About Page
  `/contact`      Contact Page
  Any other URL   404 Page Not Found

``` js
switch (req.url) {
    case "/":
        res.end("Homepage");
        break;

    case "/about":
        res.end("About Page");
        break;

    case "/contact":
        res.end("Contact Page");
        break;

    default:
        res.end("404 Page Not Found");
}
```

------------------------------------------------------------------------

# 9. HTTP Server with Logging and Routing

``` js
const http = require("http");
const fs = require("fs");

const myServer = http.createServer((req, res) => {
    const log = `${Date.now()}: New Request received`;

    fs.appendFile("log.txt", log + "\n", (err) => {
        if (err) {
            console.log("Error in writing to file");
        }

        switch (req.url) {
            case "/":
                res.end("Homepage");
                break;

            case "/about":
                res.end("About Page");
                break;

            case "/contact":
                res.end("Contact Page");
                break;

            default:
                res.end("404 Page Not Found");
        }
    });

    console.log(req.headers);
});

myServer.listen(8000, () => {
    console.log("Server is Started");
});
```

## Program Flow

**Client Request → HTTP Server → Request Handler → Log Request → Check `req.url` → Send Appropriate Response**

---

# 10. Methods and Properties Used

## OS Module

| Method | Use |
|---|---|
| `os.freemem()` | Free system memory |
| `os.totalmem()` | Total system memory |
| `os.platform()` | Operating-system platform |
| `os.hostname()` | Computer hostname |
| `os.homedir()` | User home directory |

## HTTP Module / Server

| Method / Property | Use |
|---|---|
| `http.createServer()` | Creates HTTP server |
| `server.listen()` | Starts server on a port |
| `res.end()` | Sends and ends response |
| `req.url` | Gets requested path/URL |
| `req.headers` | Gets request headers |

## File System (`fs`) Module

| Method | Use |
|---|---|
| `fs.appendFile()` | Appends data to a file |

## JavaScript Method Used

| Method | Use |
|---|---|
| `Date.now()` | Returns current timestamp |

## Module System

| Syntax | Use |
|---|---|
| `require()` | Imports/loads a module |
| `module.exports` | Exports values/functions from a module |
| `exports.name` | Exports an individual property/function |

---

# 11. Therefore,

-   `node -v` checks the Node.js version.
-   `npm -v` checks the npm version.
-   `npm init` initializes a Node.js project.
-   `nodemon` automatically restarts the application when source code
    changes.
-   A module is a reusable block of code.
-   `require()` loads a module.
-   `module.exports` and `exports` make code available to other files.
-   `os` provides operating-system information.
-   `http` is used to create an HTTP server.
-   `fs` is used to work with files.
-   `http.createServer()` creates the server.
-   The handler function receives `req` and `res` objects.
-   `req.url` identifies the requested route.
-   `req.headers` contains request-header information.
-   `res.end()` sends and ends the response.
-   `server.listen()` starts the server on a port.
-   `fs.appendFile()` can maintain a request log.
-   A `switch` statement with `req.url` can implement basic routing.
