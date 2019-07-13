# Complete_Notes_Mern_Full_Stack MERN STACK
# Complete_Notes_Mern_Full_Stack

MERN STACK

->mkdir mern-votes
go to gitignore.io
type macos,node,visualstudio -- create
copy the contents
>cd mern-votes
>touch .gitignore
copy the contents here



Server App
-->mkdir Server
>cd Server
>npm init
it will create a package.json file
remove the test script form there since we r not gonna test it

>touch index.js
console.log('hi'); //for testing
>node index.js

now install express
>npm install express

package.json and package-lock.json conatins all the dependencies that express depends on
and node modules contains all those packages


..................index.js..........................................

//create server
const express = require('express');
const app=express();

//start listing
const port= 4000; //any no. above 1000,below 1000 is used by our computers

app.listen(port, console.log()); //backtick for template literals

..................index.js..........................................


>node index.js

//send to browser
app.get('/',(req,res)=>res.send('hello world'))

......................updated code.................................
//create server
const express = require('express');
const app=express();

//start listing
const port= 4000; //any no. above 1000,below 1000 is used by our computers

app.get('/',(req,res)=>res.send('hello world'))
app.listen(port, console.log()); //backtick for template literals



>node index.js

-------go to localhost:4000 and you will see hello worlds

.............................................

//////////
other then sending us just text ,
we will help client to communicate wd the Server
using the json data
its javascript object  ***objects


app.get('/',(req,res)=>res.json ({hello :'worlds'}));//json object

>node index.js

......................updated code.................................



//create server
const express = require('express');
const app=express();
const port= 4000; //any no. above 1000,below 1000 is used by our computers

//start listing
app.get('/',(req,res)=>res.json ({hello :'worlds'}));//json object



app.listen(port, console.log()); //backtick for template literals

''''''''''''''''''''''''''''''''''''''''''''''''''''
>node index.js

go to localhost:4000

you will see

{hello:worlds} //json object

-------------------------------------------------------Error handler

lets actually create an error handler

almost all of express methods like app.get(),use() expect middleware function
app.get('/',(req,res)=>res.json ({hello :'worlds'}));

in the above eg: (req,res)=>res.json ({hello :'worlds'}) is a middleware function
app.get('/',(req,res),next)
its has three parameters res,req,next

NEXT IS VERY IMPORTANT FOR ERRORS

//next is ver imp to errors
app.use((req,res,next)=>{
    const err = new Error('not found');
    err.status=404;

    next(err);//sending in  that error to next function
})


//we have to have a middle ware technically it is an after ware
//cauz its runs after every request finishes ,it runs just before the app crashes
//its the final end point where the server lands before app crashes
app.use( (err,res,req,next)=> {
    res.status(err.status || 500).json(//500 for any diff error
        {
            err: err.message || 'Something went wrong'
         }
    );
});
......................updated code using bodyParser.................................

//create server
const express = require('express');
const app=express();
const port= 4000; //any no. above 1000,below 1000 is used by our computers

//start listing
app.get('/',(req,res)=>res.json ({hello :'worlds'}));//json object


//next is ver imp to errors
app.use((req,res,next)=>{
    const err = new Error('not found');
    err.status=404;

    next(err);//sending in  that error to next function
})


//we have to have a middle ware technically it is an after ware
//cauz its runs after every request finishes ,it runs just before the app crashes
//its the final end point where the server lands before app crashes
app.use( (err,res,req,next)=> {
    res.status(err.status || 500).json(//500 for any diff error
        {
            err: err.message || 'Something went wrong'
         }
    );
});

app.listen(port, console.log()); //backtick for template literals
''''''''''''''''''''''''''''''''''''''''''''''''''''


>node index.js
go to the route that doesnot exist
localhost/anything

TypeError: res.send is not a function ###33333333333333 error check this


output should be:
{
err: 'not found'
}




''''''''''''''''''''''''''''''''''''''''''''''''''''


# Complete_Notes_Mern_Full_Stack
