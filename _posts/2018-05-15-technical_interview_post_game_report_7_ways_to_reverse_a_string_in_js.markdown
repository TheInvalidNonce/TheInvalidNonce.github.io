---
layout: post
title:      "Technical Interview: Post Game Report (5 ways to reverse a string in JS)"
date:       2018-05-15 23:43:25 -0400
permalink:  technical_interview_post_game_report_7_ways_to_reverse_a_string_in_js
---


I recently had a series of 4 in-person interviews for a Mobile Web Engineer position at the Dow Jones, specifically on the Wall Street Journal team. I had the luxury of tackling my technical interview first out a series of 4 consecutive (3 mostly cultural, 1 technical) interviews with the wonderful people who make the magic happen at the Wall Street Journal. 

Among one of the questions I was asked during the technical interview was reversing a string in Javascript in various ways. I was tasked with whiteboarding out a function that reversed a string in place at first, followed by implementing my solution without using the built-in functions that allows you to split a string into an array, reverse the array, and then join the string back and return it. 

I'll be discussing some useful approaches one can keep in mind to approach this whiteboarding problem.

1: Using built-in functions:

```
const reverse = str => {
  return str.split('').reverse().join('')
}
```

This version takes advantage of the ‘reverse()’ method provided by the Array prototype in Javascript. First it splits the string into an array, then calls the ‘reverse()’ method and finally returns the joined array.

2: Decrementing for-loop with concatenation

```
const reverse = str => {
  let newStr = ''
  for (let i = str.length - 1; i >= 0; i--)
    newStr += str[i]
  return newStr
}
```

Here we use a decrementing for-loop that appended each character of the input to a new string in reverse order starting with an empty string. Here you add the individual characters similar to the way you would reference an array’s items.

3:  Incrementing for loop with array pushes and charAt:

```
const reverse = str => {
  let arr = []
  for (let i = 0, i <= str.length; i++)
    arr.push(str.charAt(str.length - i))
  return arr.join('')
}
```

Here we use one incrementing value that gets deducted from the total length of the parsed in string. This calculated value determines the position of the next character to be added onto the new array (using the ‘push()’ function instead of ‘[]’).

4: Decrementing while loop with concatenation and the substring String prototype method

```
const reverse = str =>{
  let i = s.length,
  let newStr = ''
  while (i > 0) {
    newStr += str.substring(i - 1, i)
    i--
  }
  return newStr
}
```

Here we use a decrementing while loop. Using the power of string concatenation, I was able to implement a similar solution in a similar fashion to the for-loop used in the previous two examples. I was then able to use the very unpopular String prototype ‘substring()’ function to retrieve each desired character.

5:  Recursion with the substring and charAt methods with ternary operators

```
const reverse = str {
  return (str === '') ? '' : reverse(str.substring(1)) + str.charAt(0)
}
```

Recursion is a concept where you call the function being declared is called on itself in the body of the function. This example recursively calls itself, passing itself in the inputted string, excluding the first character on each iteration, which is instead appended to the result. This process then repeats itself until no input is present (the base case) which results in a reversed string.









