---
layout: post
title:      "Rails Project: Coinance"
date:       2018-02-07 14:13:08 -0500
permalink:  rails_project_coinance
---

# **Intro**

[Coinance](https://coinance.herokuapp.com) (pronounced *Coin-ance*) is a Ruby on Rails web application that allows you to manage a portfolio of your digital currency assets and investments. My inspiration for this app came from my years of interest in blockchain technology and crypotcurrencies. With the numerous websites coming and going that dealt with every single cryptocurrency, I saw an opportunity to create something meaningful for my Rails Project.

This project called for a significant increase in compelxity and planning from my previous [Sinatra project](https://github.com/TheInvalidNonce/TrackBeer). The requirements were similar to the Sinatra project, but much more specific in regards to how to set it up, and also how your models needed to be structured. Also, the complexity and under-the-hood magic that is the Rails framework meant that you had to truly understand many of its subtle nuances of how it brings all the working parts of an application together.

# **Features**

* Live demo deployed to [Heroku](https://coinance.herokuapp.com)
* Users can create an account to store data on transactions and wallets where they have any cryptocurrencies.
* Leverages the [Cryptocompare API](https://www.cryptocompare.com/api/) to retrieve real-time info & price data on 2,000+ cryptocurrencies and tokens.
* Users can save a transaction or a wallet by selecting from a real-time list of digital currencies and tokens to save to the database.
* Coins are selected in real-time, and persisted to the database as an associated coin to either a wallet, or a transaction.
* Users can submit their own prices if purchased at a different time for their own transactions/wallets.
* User sign-in, sign-out, and session security is handled with Devise [Devise](https://github.com/plataformatec/devise)
* Users can log in with Facebook using [Omniauth](https://github.com/omniauth/omniauth)
* Displays updated price data on Bitcoin, Ethereum, and Litecoin on the Coin index page.
* Displays stats on the Coins saved with the most transactions.
* Users can ONLY create, read, update, or delete their own transactions and wallets.
* All user data is validated using ActiveRecord ORM & Rails model validations.
* Database schema is created in PostgresQL.
* Styled custom SCSS with an open-source [Bootstrap theme](https://bootswatch.com/lux/).

# **Application Development Workflow**
## **Planning For Success **

Before I wrote any code and having read about the many issues new Rails coders would muse about on Slack, I decided to think long and hard about what Models I planned to have, what attributes they would contain, and how all of this data would interact with one another in a database. I knew from the outset that this type of project would be the most extensive one I have written to date, and making sure I truly understood my model object associations would be paramount to a constructive workflow.

I also wanted to go above and beyond and integrate an API for this project to get real-time Coin & Token info. I ended up using a [CryptoCompare gem](https://github.com/alexanderdavidpan/cryptocompare) that helped to make the API calls to retrieve data on the coins I requested. As I was getting closer to finishing up a fully working app, I could have just used my own code since I had to create many custom methods to retrieve the exact data I wanted.

I used a (now rarely free) [Diagram App](https://www.draw.io/) to begin drawing out my Models and Associations. I settled on having 5 models: User, Coin, Transaction, Wallet, and model for the API called CryptocompareApi.

## **No Scaffolding**

One of the first requirements for the project was to refrain from using the Rails command for generating scaffolding for the project. What this means is that after you generate a new Rails app with

`rails new <AppName>` 

you can quickly get to work and have a boilerplate CRUD app with a DB migration, Model, Views, and associated Controller in seconds by using:

`rails generate scaffold <model_name>`

As frustrating as this was, it served a purpose: To allow us to understand each and every part of the app, and remove any unnecessary bloat that comes from the command since for every model you send it, it will provide most of the work you will be building and not give you the iterative nature of building an app from the ground up, which is how you really learn.

In addition, we were still able to generate resources (such as empty base models, controllers, and migrations, which in the end was actually more useful since it did not create any unnecessary views and code.

To be continued...



