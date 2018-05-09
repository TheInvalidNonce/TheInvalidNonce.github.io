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
[GraphQL](http://graphql.org/) is a data query language developed internally by Facebook in 2012, that was then released to the public in 2015. It provides an alternative to REST and ad-hoc webservice architechtures. t allows clients to define the structure of the data required, and exactly the same structure of the data is returned from the server. It is a strongly typed runtime which allows clients to dictate what data is needed. This avoids both the problems of over-fetching as well as under-fetching of data. The two most popular GraphQL clients are Relay, which is also made by Facebook, and Apollo, which is an open-source community-driven alternative.

# Why GraphQL?
There are several advantages of GraphQL as opposed to normal SQL-based relational databases.

**GraphQL is declarative:**: You ask for what you need, and get exactly that. Query responses are served by the client instead of the server. 

**GraphQL is compositional**: Get many resources in a single request. While typical Rest APIs require loading from multiple URLs, GraphQL APIs get all of the data it needs in a single request. Apps using GraphQL can be quick even on a slow mobile network connection.

**GraphQL is strongly-typed**: GraphQL APIs are organized in terms of types and fields, not endpoints. Access the full capabilities of your data from a single endpoint. GraphQL uses types to ensure Apps only ask for what’s possible and provide clear and helpful errors. Apps can use types to avoid writing manual parsing code.

# Node/Express setup

# GraphQL

# Relay vs Apollo

# React Front end
