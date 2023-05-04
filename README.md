# primera-API-express
Solution to "Mi primera API con express" project of Make It Real.

## Process

### Starting with Express

- Initialization of express with `npm init -y` on the console, then installing express with `npm install express`.
- In the *package.json* that was created you can see as the value of *"main"* *"index.js"* set by default, it's in that repository that I created the whole exercise.
- Under/inside *scripts* in the *package.json* I create a new script that is going to allow me to start the server and when there's any change is going to recharge the server:
```
"dev": "node --watch index.js"
```
The script is named *dev* and executes *index.js* but it's flagged with *--watch* an experimental option that allow us to retart a server of Node.js when changes are detected in the specific file. This was made before recent updates with other libraries (e.g. *nodemon*).

### Using express

- In the js file we call/require express with `const express = require('express')` and then we assigned it by convention to the variable `app` as `const app = express();`.
- Then I set the port that we are going to be using: `const port = 3001;` and set express to listen to that port: 
```
app.listen(port, () => console.log(`Example app listening on port ${port}`));
```

### Route handling

- We use `app.verb()` method replacing verb with the http method needed, and inside it receives two parameters `('/PATH' , callback)` being the first one the path that follows the main *URL* and the second one a callback function called *route function* that receives two parameters `(req, res)` being *request* and *response* respectively.

- When a request is received in a certain path the *route function* is called, and then `req` contains information about the HTTP request (e.g URL, Method, Headers...). And `res` it's used to send answers to the client. 

### HTTP Status codes

- I used a image reference:

![Status-codes](https://raw.githubusercontent.com/mercuryeater/primera-API-express/main/public/http-status-code-poster.png)

### morgan middleware

- It's a middleware logger to every HTTP request made on an app.

- Installing it with `npm install morgan` on the console.

- Using it/Calling it on the app with: `const morgan = require('morgan')`

- morgan it's called with `app.use(morgan())` and receives `( format, options)`, in the format argument you can use a *predefined* format string (e.g. combined, common, dev, short, tiny), a format string of predefined tokens (e.g. :method :url :status :response-time ms) and a custom format function that I didn't look too much but can be looked up on the [doc](https://expressjs.com/en/resources/middleware/morgan.html).

- Creating a custom token to be able to print the body being sent on POST request by writing:
```
morgan.token('body', function (req) { return JSON.stringify(req.body) })
```
Where the `'body'` it's the name I'm giving it, and the fuction is listening to the *request* and returning the *body* of that request transformed to a string in format JSON. The `JSON.stringify()` takes an object and returns a JSON string that can be sent through the web or stored in a database.
### First time using:

- `Math.floor`: Used to round down a number to an integer that it's less than or equal tothe given number.

- `Math.random()`: Used to give a random number between *0* and *1*. And in the code I multiplied by 1'000.000 so there's little chance to have a repeating number.

- **morgan middleware**: Used to -register- create logs on the server console, everytime there is a request on the URL/Server app. We can set what to print, it has it's own part on this readme.

