---
layout: post
title:      "My journey into Node, Express, GraphQL and Relay"
date:       2018-05-08 23:58:14 -0400
permalink:  my_journey_into_node_express_graphql_and_relay
---


I was recently sent a code challenge to build out an app where I create a Node/Express backend with GraphQL, & an interface of my choice and have that be my API endpoint for my React frontend. This blog post will go into detail on how I approached it and what some of the struggles were in implementing them.

# The Challenge
Using React, GraphQL and your choice of GraphQl client (we use Relay but you are no required), create an API from which you can query from to display books. We have a attached a JSON file of 100 books to use. The user should be able to display 10 books initially, paginate through the books and also perform a fuzzy search. The books should display in a grid format. When complete please push your code to a Github repo and provide a link.

# Acceptance Criteria
Display 10 books at a time.
Allow the user to paginate through the books.
Allow the user to search through the books by title.
Style the grid and layout
# Bonus Criteria (optional)
Create units tests for created components.
Allow the user to click into an individual book page and display more details

Note:
If you don’t have experience with GraphQL, feel free to build API using Node.JS and use it in React Components.

# Intro
[GraphQL](http://graphql.org/) is a data query language developed internally by Facebook in 2012, that was then released to the public in 2015. It provides an alternative to REST and ad-hoc webservice architechtures. It allows clients to define the structure of the data required, and exactly the same structure of the data is returned from the server. Its a strongly typed runtime which allows clients to dictate what data is needed. This avoids both the problems of over-fetching as well as under-fetching of data. The two most popular GraphQL clients are Relay, which is also made by Facebook, and Apollo, which is an open-source community-driven alternative.

# Why GraphQL?
There are several advantages of GraphQL as opposed to normal SQL-based relational databases.

**GraphQL is declarative:**: You ask for what you need, and get exactly that. Query responses are served by the client instead of the server. 

**GraphQL is compositional**: Get many resources in a single request. While typical Rest APIs require loading from multiple URLs, GraphQL APIs get all of the data it needs in a single request. Apps using GraphQL can be quick even on a slow mobile network connection.

**GraphQL is strongly-typed**: GraphQL APIs are organized in terms of types and fields, not endpoints. Access the full capabilities of your data from a single endpoint. GraphQL uses types to ensure Apps only ask for what’s possible and provide clear and helpful errors. Apps can use types to avoid writing manual parsing code.

# Node Server setup
To setup a Node.js GraphQL server, we create a new empty project folder:

```
mkdir graphql-server
```

Switch to that directory and we initialize a new `package.json` file by running:

```
npm init
```

Next, we create the new `server.js` file in the server directory. 

```
touch server.js
```

Alternatively, the '>' character in the Bash prompt is a `touch` alias:

```
> server.js
```

Finally we add the graphql, express, and express-graphql NPM packages to our project:

```
npm install graphql express express-graphql -save
```

You have now installed the proper dependencies to get server code started. On to Express!

# Implementing a Simple GraphQL Server with Express
Lets begin by adding this code into  `server.js`

```
const express = require('express')
const expressGraphql = require('express-graphql')
const schema = require('./schema/schema')
const cors = require('cors')

// Create the express server
const app = express()

// This is to allow Cross Origin Resource Sharing for the purposes of this example app
app.use(cors())

// Create the GraphQL endpoint of the Express server
app.use(
  '/graphql',
  expressGraphql({
    schema,
    graphiql: true
  })
)

app.listen(4000, () => console.log('Express GraphQL Server Now Running on localhost:4000/graphql'))
```

Let me explain what this block of code is doing. First we need to make sure that express, express-graphql, the schema (which I will build next), and cors packages are imported. 

The Express server is created with a GraphQL endpoint: '/graphql'. We first need to store a new express instance in app. We then create the GraphQL endpoint and then utilize the app.use method call and pass it two parameters:

1. The URL endpoint as a string
2. A configuration object passed into the call of the express_graphql package containing two properties.

The two configuration properties that are used for the Express GraphQL middleware are:

1. `schema`: The GraphQL schema which should be attached to the specific endpoint
2. `graphiql`: This is set to true to enable the GraphiQL data visualization tool. GraphiQL is an in-browser graphical interactive IDE . This tool is critical to writing queries in the browser and also test your endpoint out.

Finally, `app.listen` starts our server on port 4000.

To start this server you can use either:

```
node server.js
```

or while in the server folder:

```
yarn install
```
```
yarn start
```

If you go to `localhost:4000/graphql` you should see this:

![GraphuQL interface](https://cdn-images-1.medium.com/max/1600/0*TiL2iv3w7719s4GV.png)
# Relay vs Apollo

# React Front end
