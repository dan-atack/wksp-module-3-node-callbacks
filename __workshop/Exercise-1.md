# Questions

**With a partner**, answer these questions as completely as possible. Feel free to look at past lecture notes, the web, anything.

Take the time to explain it to each other.

The power of this exercise is in the act of _formulating_ and _explaining_ the concepts to someone else (your teammate).

## One

Run the app. Write out the steps, the _pseudo code_, required to create this app. It doesn't have to be totally accurate, or in the right order.

Only move on to the next question when you have enough detail that you would be able to start coding it yourself.

SERVER.JS
importing dependencies
initialize express and middleware
declare endpoints
and 404
run the server

HANDLER.JS
passing data and functions to the page

PAGES
HP.EJS
404.EJS

PARTIALS
HEADER.EJS
FOOTER.EJS
TODOINPUT.EJS (form is created)

PUBLIC
STATIC HTML
CSS

## Two - `server.js`

Take a look at the `server.js` file.

We have a new module in there, `body-parser` that is required on line `4`. What is it for? What is its use-case? What other lines are related to this module?

_The NPM site might be a good place to start. Feel free to provide links as relevant._

```
The  body-parser  allows express to read the body and then parse that into a Json object that can be read and interpreted. It is a middleware that facilitates the passing of data by parsing the json.

it is initialized at the top
then launched?? used at the bottom

```

## Three - `server.js`

Look at lines `26` and `27`. Explain the methods used. How are they different? What are the usecases for each?

The get retrieves or renders the homepage
.get("/", handleHomePage)
The post retrieves or renders the form that can be edited and submitted
.post("/form-data", handleFormData)

```

## Four - `server.js`

Line `6`. That's new. What do you think it's for?

this below determines the order of handling the pages, first we will get homepage, then allow editing of form and if not the first two we get the 404 error
const { handleHomePage, handleFormData, handle404 } = require("./handlers");



```

## Five - `handlers.js`

Explain line `1`. Where, why and how is `items` being used?

const items = [];
We are declaring an empty array so that items filled in will be delivered as an array

```

## Six - `handlers.js`

Why is there `redirect` on line `11`;
if the above functions are not fulfilled then we are redirected to homepage
    res.redirect('/');



```

## Seven - `handlers.js`

The `handle404` function is a more complex than we've seen thus far, what is the extra functionality for?
if (req.accepts('html')) {
res.render('pages/fourOhFour', { path: req.originalUrl });
return;
}

// respond with json
if (req.accepts('json')) {
res.send({ error: 'Not found' });
return;
}
There are two different error pages. The one that accepts html renders a 404 page. The other accepts json and sends a not found message

## Eight - `ejs`

Take a look at `homepage.ejs` and `todoInput.ejs`. What is happening in there? Explain line-by-line...
`homepage.ejs`
<%- include('../partials/header') %>
//above header partials is retrieved

<div class='input-container'>
    <%- include('../partials/todoInput') %>
    // todoInput file is retrieved
</div>
<div class='content'>
//the div will be styled by the content class
    <ul class='todo-list'>
    // an unordered list is formed
        <% items.forEach(item => { %>
            <li class='todo-list--item'><%= item %></li> 
            it making list appear as an array we are declaring these items in the array
        <% }); %>
    </ul>
</div>
<%- include('../partials/footer') %>
//above footer partials is retrieved

in todoInput.ejs
is where the form is created with a POST action that allows users to add/ edit info
and input with submit button

<form method='POST' action='/form-data'>
    <label for='item'>TODO Item</label>
    <input type='text' name='item' placeholder='Item Description' />
    <button type='submit'>Submit</button>
</form>

```



```

```

```

```

```
