---
layout: post
title:      "Code Challenge : Remove Empty Fields from a JSON Object"
date:       2018-05-22 23:53:32 -0400
permalink:  code_challenge_remove_empty_fields_from_a_json_object
---


At the beginning of this weekend I was sent another coding challenge to prove that I can actually code as well (or better) as I claim I can. This coding challenge was for an entry level software developer position at a social media marketing platform. 

The goal of the challenge was to remove empty fields from a given JSON object. The concept is pretty straightforward however the implementation took a bit of tweaking in order to achieve the desired result.

First, what is JSON you ask? And why should I care? Well, JSON is short for **J**ava**S**cript **O**bject **N**otation. It is a syntax for storing and exchanging data between a browser and a server and is one of the most frequently used data structures you will see as a developer. 

In addition to it being (initially) a basic Javascript object, its structure and versatility has paved the way for NoSQL databases like MongoDB to utilize its non-relational and highly scalable data model structure. Since the JSON format is text only, it can easily be sent to and from a server, and used as a data format by any programming language.

With that said, lets dive into the challenge.

# The Objective
Write a function that can remove **all** fields with an **empty** value, from **any** JSON input.
The solution must be reusable for processing any kind of JSON input, e.g., the JSON field
structure and names may change in the future.

The following values are considered empty:
* null
* An empty array or []
* An empty object or {}
* An empty string, such as "" or " "


# The Input Object
'{
"first_name": "Mike",
"last_name": "Gordon",
"email": "mike.gordon@phish.com",
"talents": null,
"skills": [
{
"drums": "",
"keyboard": null
}
],
"company": {
"name": "",
"scarves": []
},
"address": {
"city": "New York",
"state": "NY",
"zip": "10023",
"street": " "
}
}'

# The Expected Output
'{
"first_name": "Mike",
"last_name": "Gordon",
"email": "mike.gordon@phish.com",
"address": {
"city": "New York",
"state": "NY",
"zip": "10023"
}
}'

# My Approach
One way to think of a JSON object is a bunch of key/value pairs that can exhibit levels of nesting. This particular input had many levels of nested null, or invalid values that meant that they had to be parsed through without knowing how nested these objects could be.

I started by coding out my function by iterating through the whole object:

```
const removeEmptyFields = (obj) => {
      if (obj[i] ===  ''|| obj[i] === ' ' || obj[i] === null) // Check if empty string, 1 character empty string, or null
        console.log('deleting:', obj[i]) // Log out what is being removed
        delete obj[i]
      }
    }
  return obj
}
```

Here I started out by using the ES6 `for` loop construct that allows you to loop through an object. In this iteration, I went through the object and began by checking if an object's value `obj[i]` contained a `null` value or an empty string or an empty string with one whitespace character.

This is a good start, until you realize that this only works for items only one level deep. All of the nested invalid items are not being removed. This is a quickly becoming a problem.

The philosophical question of how does one iterate though an object when you don't know how deeply nested its key/value pairs can be pretty abstract to think about when first understanding the fundamentals of programming.

In order to keep iterating through the object without knowing its structure beforehand requires a frequently seen computer science called recursion.

# Recursion
Recursion is a concept used in most programming languages. The basic notion of it is that you can call a function within itself. This may seem a bit foreign but once you get used to it, it can be a very powerful tool in your programming arsenal. 

For the sake of brevity, I'll leave this [Wikipedia link](https://en.wikipedia.org/wiki/Recursion_(computer_science)) on the topic if you want a deeper understanding. 

The main concept to grasp is that calling a function within itself is fine as long as you have a conditional base case to prevent the computer from trying to create a nonstop 
