```javascript
console.log(module)
```

```json
Module {
  id: '.',
  path: '/Users/mac',
  exports: {},
  filename: '/Users/mac/test.js',
  loaded: false,
  children: [],
  paths: [ '/Users/mac/node_modules', '/Users/node_modules', '/node_modules' ]
}
```

```javascript
const path = require('path')
var pathObj = path.parse(__filename);
console.log(pathObj)
```

```json
{
  root: '/',
  dir: '/Users/mac',
  base: 'test.js',
  ext: '.js',
  name: 'test'
}
```

```javascript
const fs = require('fs')

//Sync
console.log(files);
const files = fs.readdirSync('./');

//Async
fs.readdir('./', function (err, files) {
    if(err) console.log("Error", err)
    else console.log('Result',files)
})

```

```javascript
//Main.js
const EventEmitter = require('events')

const Logger = require('./logger');
const logger = new Logger();

logger.on('messageLogged', (arg) => {
   console.log('Listener called', arg);
});

logger.log('message')
```

```javascript
//logger.js

const EventEmitter = require('events');
const emitter = new EventEmitter();

var url = 'http://mylogger.io/log'

class Logger extends EventEmitter{
    log(message) {
        console.log(message);
        this.emit('messageLogged', {id:1});
    }
}

module.exports = Logger;
```

```javascript
//Main.js

const http = require('http');
const server = http.createServer();

server.on('connection', (socket) => {
    console.log("New Connection")
})

server.listen(3000);

console.log("Listening on port 3000")
```

```javascript
//Main.js

const http = require('http');
const server = http.createServer(function(req, res){
    if(req.url ==='/'){
        res.write('Hello World');
        res.end();
    }
});

server.listen(3000);

console.log("Listening on port 3000")
```

## Express

```javascript
const logger = require('./logger')
const express = require('express');
const app = express();

app.use(express.json());

app.use(logger);

const courses =[
    {id:1, name:'course1'},
    {id:2, name:'course2'}
]

app.get('/', (req,res)=>{
    res.send("Hello World");
})

app.post('/api/courses', (req, res) => {
    const course = {
        id: courses.length + 1,
        name: req.body.name
    }
    courses.push(course);
    res.send(course);
})

app.get('/api/courses/:id', (req, res) => {
    const course = courses.find(c => c.id === parseInt(req.params.id));
    if (!course) res.status(404).send("The course with the given ID was not found");
    res.send(course);
})

const port = process.env.PORT || 3000;
app.listen(3000, () => console.log("Listening on port 3000"))
```

```javascript
//logger.js
function log(req, res, next){
    console.log('Logging....');
    next();
}

module.exports=log;
```

