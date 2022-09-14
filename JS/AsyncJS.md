```javascript
console.log("Before");
const user = getUser(1);
console.log(user);
console.log("After");

function getUser(id){
    setTimeout(()=>{
        console.log("Reading user from database");
        return {id: id, githubUserName: 'mosh'}
    }, 2000)

    return 1;
}
```

```
/Users/mac/.nvm/versions/node/v18.7.0/bin/node /Users/mac/WebstormProjects/MyProject/async.js
Before
1
After
Reading user from database

Process finished with exit code 0
```

```javascript
console.log("Before");
getUser(1, function(user) {
    console.log('User', user);
});
console.log("After");

function getUser(id,callback){
    setTimeout(()=>{
        console.log("Reading user from database");
        callback({id: id, githubUserName: 'mosh'});
    }, 2000)
}	
```

```
/Users/mac/.nvm/versions/node/v18.7.0/bin/node /Users/mac/WebstormProjects/MyProject/async.js
Before
After
Reading user from database
User { id: 1, githubUserName: 'mosh' }

Process finished with exit code 0
```

```javascript
console.log("Before");
getUser(1, (user) => {
    getRepositories(user.githubUserName, (repos) => {
        console.log('Repos',repos);
    })
});
console.log("After");

function getUser(id,callback){
    setTimeout(()=>{
        console.log("Reading user from database");
        callback({id: id, githubUserName: 'mosh'});
    }, 2000)
}

function getRepositories(username, callback){
    setTimeout(() => {
        console.log("Calling Github Api ....");
        callback(['repo1','repo2','repo3'])
    })
}
```

```
/Users/mac/.nvm/versions/node/v18.7.0/bin/node /Users/mac/WebstormProjects/MyProject/async.js
Before
After
Reading user from database
Calling Github Api ....
Repos [ 'repo1', 'repo2', 'repo3' ]

Process finished with exit code 0
```

