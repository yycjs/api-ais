title: Better APIs and smarter AIs
output: index.html
theme: theme
controls: false
logo: theme/logo.png

--

# Better APIs and smarter AIs

## YYCJS summer finale

-- sponsors

# Our Sponsors

![Assembly](img/sponsors/assembly_logo.png)

![Village Brewery](img/sponsors/village_brewery_logo.png)

![Startup Calgary](img/sponsors/startup_calgary_logo.png)

![PetroFeed](img/sponsors/petrofeed_logo.png)

--

# This year

* [9 years of JavaScript](http://www.meetup.com/yyc-js/events/222682792/)
* [React in the real world](http://www.meetup.com/yyc-js/events/221664814/)
* [Modular JavaScript & ArangoDB](http://www.meetup.com/yyc-js/events/221663824/)
* [Ruby vs. JS - Building an API and making it real-time](http://www.meetup.com/yyc-js/events/221583296/)
* [The perfect JavaScript project](http://www.meetup.com/yyc-js/events/220713495/)
* [Learning JavaScript](http://www.meetup.com/yyc-js/events/220256403/)
* [HTML500](http://www.meetup.com/yyc-js/events/220071200/)
* [Back to the future](http://www.meetup.com/yyc-js/events/219630216/)

--

# Brought to you by

-- presenter

![David Luecke](http://gravatar.com/avatar/a14850281f19396480bdba4aab2d52ef?s=200)

## David Luecke

* [<i class="fa fa-github"></i> daffl](https://github.com/daffl)
* [<i class="fa fa-twitter"></i> @daffl](http://twitter.com/daffl)

-- presenter

![Eric Kryski](http://gravatar.com/avatar/23aba778a7daae99348aeb0728cf4aec?s=200)

## Eric Kryski

* [<i class="fa fa-github"></i> ekryski](https://github.com/ekryski)
* [<i class="fa fa-twitter"></i> @ekryski](http://twitter.com/ekryski)
* [<i class="fa fa-home"></i> erickryski.com](http://erickryski.com)

--

# Feathers

--

## A REST and real-time API + MongoDB

10 lines, no generators, no magic

```javascript
// npm install feathers feathers-mongodb body-parser
var feathers = require('feathers');
var bodyParser = require('body-parser');
var mongodb = require('feathers-mongodb');

var app = feathers()
  .configure(feathers.rest())
  .configure(feathers.socketio())
  .use(bodyParser.json())
  .use(feathers.static(__dirname))
  .use('/todos', mongodb({
    collection: 'todos'
  }));

app.listen(8080);

app.service('todos').create({
  text: 'A Todo created on the server'
  complete: false
});
```

--

## Client use

[feathers-client]() is a JavaScript client that connects to REST or real-time Feathers services. Use it on other NodeJS server, with libraries like [jQuery]() or client side frameworks like [React](), [Angular]() or [CanJS]():

```javascript
<script src="socket.io/socket.io.js"></script>
<script src="node_modules/feathers-client/dist/feathers.js"></script>
<script type="text/javascript">
  var socket = io();
  var app = feathers().configure(feathers.socketio(socket));
  var todos = app.service('todos');

  todos.on('created', function(todo) {
    console.log('New Todo created: ' + todo.text);
  });

  todos.create({
    text: 'Todo created on the client',
    complete: false
  });
</script>
```

--

# Demo: Real-time Todos with Feathers + React

--
