---
layout: post
title:      "Coinance: jQuery Edition (or how I learned to grow patient with undefined)"
date:       2018-03-12 14:43:08 +0000
permalink:  coinance_jquery_edition_or_how_i_learned_to_grow_patient_with_undefined
---

## Intro
For the 4th Portfolio Project in this coding journey, we were tasked with adding jQuery and Javascript to our already existing Rails portfolio project. This was a unique Porfolio Project concept since up until now, we all had to create an entire app from scratch. However, to mimic a more authentic software development experience where we are adding a new feature to an already existing app structure.

## Requirements
The requirements for this project were pretty straightforward, however, the implementation of them called for a new level of patience in a language that I have been trying to learn for years even before my time here at Flatiron. That beast is also known as Javascript. I can say that even with exposure to the language for several years now, but actively grinding out the core fundamentals of it the past couple of months led to a love/hate relationship with Javascript, and how many times when working with it. You will see the useful, but sometimes, infurating object known as 'undefined'.

## undefined undefined UNDEFINED!?
What does undefined mean in the world of Javascript? 

```
undefined is a property of the global object; i.e., it is a variable in global scope. The initial value of undefined is the primitive value undefined.
```

OK, what does that mean *really*?

```
A variable that has not been assigned a value is of type undefined. A method or statement also returns undefined if the variable that is being evaluated does not have an assigned value. A function returns undefined if a value was not returned.
```

What this means is that you can declare a variable like so:

```var a;```

It's technically declared, but of type ```undefined```. It will only gain a type after an assignment to a value.

To further elaborate on this, a function will ALSO return undefined if it does not return a value. What this means that you have a function:

```
function foo(x) {
  var x = 2
	x += 2
}
```

This will return undefined since the function is not explicitly returning anything even when passed in an argument. **Only** when there is a `return` statement, **OR** a function such as `.map`, or in jQuery `.done` after an `.ajax` request, will there be anything returned in order to evaluate the statement being returned. Until then, even this valid function will be of type undefined since it will not explicitly, or even implicitly return a value.

I found some difficulty making sense of it all, and it honestly took a significant amount of trial and error in my code, and dropping `debugger` statements all throughout my functions to really get a grasp of the differences in how `nil` works in Ruby, and `undefined` in Javascript. Again, the function of each both somewhat represent similar concepts, but since JS has also a `null` object, it can also be likened to Ruby's `nil`

## Life Pro Tip: debugger
What allowed me to keep my sanity when the JS/jQuery functions I was creating did not behave how I had expected them to, here comes the all mighty `debugger`. 

This tool is paramount to truly understanding the code and functions therein. From the Mozilla Developer Network (also one of the best JS resources to make sense of it all):

```
The debugger statement invokes any available debugging functionality, such as setting a breakpoint. If no debugging functionality is available, this statement has no effect.

function potentiallyBuggyCode() {
    debugger;
    // do potentially buggy stuff to examine, step through, etc.
}
```
This tool allowed me to fully understand what each line of my code was doing at that moment in time. In tandem with Chrome's inspect tools, most of my logic and function returns were able to be manipulated at the moment in time this awesome statement was dropped. 

Do yourself a favor, just use it. 

## Final Thoughts
I found this project really helped to improve my Javascript/jQuery skills significantly. I feel that I can understand my code much better, be mindful of the code I am writing, and really get to think about why I am writing the code that I am. I look forward to the React/Redux section and really getting into the fun stuff.



