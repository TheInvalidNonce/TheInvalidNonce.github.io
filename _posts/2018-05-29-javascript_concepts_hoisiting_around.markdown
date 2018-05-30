---
layout: post
title:      "Javascript Concepts: Hoisiting Around"
date:       2018-05-30 03:45:34 +0000
permalink:  javascript_concepts_hoisiting_around
---

When you are getting started with JavaScript, you may have heard of the term hoisting before. Hoisting, to put it simply, is when variable declarations in a piece of code are brought up to the top of your code. Not literally of course, because that would actually be magic.

Here we’ll create a function, then execute it:

```
const meow = sound => {
  console.log(sound)
}
meow('purr')
```

As expected when we invoke our `meow` function  ( passing in a string of our choice), that string is logged to the console. In this case, `'purr'`.

```
meow('purr')
// purr
```

However, what happens if we invoke(execute) our function before we declare it?

```
meow('purr')
const meow = sound => {
  console.log(sound)
}
```

While its not entirely clear at first, `'purr'` is logged to the console.

```
meow('purr')
// purr
```

This is essentially what hoisting is.

So, what is this madness? Your code isn't physically changing location. It all has to do with how Javascript makes several passes of your code in the blink of an eye. Javascript essentially has two phases: 1) Declaration - the phase where all of your variable declarations and assignments are done in order to give the compiler context on what to operate on. The second phase is 2) Execution. This is the phase where Javascript executes all of the code onto the variables, assignments, and references in which you have declared in the 1st phase.

In the example above, since our function declaration was added to memory during the declaration(compile) stage, we’re able to access and use it in our code.

Another example:

A typical use case where you declare and initialize a variable and then attempt to use it:

```
let a = 7
console.log(a)
// 7
``` 

However what would happen if we declare our variable at the bottom of our code?

```
a = 7
console.log(a)
let a
// 7
```

This particular example logs `7` to the console.

Here's another thought: what happens when we declare and initialize our variable at the bottom of our code?

```
console.log(a)
let a = 3
// undefined
```

What the deuce?! We expected `7`, but instead its returning `undefined`

Whats going on here? The reason is because JavaScript only hoists declarations. Initializations are not hoisted.


To make this concept a bit more reasonable: Lets say we declare and initialize a variable, say `let a = 7`, only the `let a` portion (the declaration) is going to be hoisted. The `a = 7`; (the initialization part) is not hoisted and therefore not added to memory.

If you recall, when we declare a variable but don’t initialize it, the variable is automatically set as `undefined `. 

Lets take a look at the code below only the `let a;` part will be hoisted:

```
console.log(a)
let a = 7
// undefined
```

In fact, the above code yields the same result as writing it like so:

```
let a
console.log(a)
a = 7
// undefined
```

# Conclusion
Javascript's characteristic of hoising variables is exactly why it’s considered a best practice to always declare your variables at the top of their respective scopes. Doing so is one way of minimizing undesirable effects in your code. You should also always try to initialize variables when you declare them. I hope this helps anyone understand one of the many peculiar things Javascript does!


