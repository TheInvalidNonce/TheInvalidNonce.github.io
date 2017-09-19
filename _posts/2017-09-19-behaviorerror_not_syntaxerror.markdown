---
layout: post
title:  "BehaviorError, not SyntaxError "
date:   2017-09-19 13:56:39 -0400
---


For the past few days I have been working on a program of Tic Tac Toe in Ruby with a command line interface (CLI) component, that also has an computer (AI) component. This program is meant to be a digital version of Tic Tac Toe with 3 options: 1) Human vs Human, 2) Human vs Computer, and 3) Computer vs Computer.

Overall, coding up this particular program was good practice since, in previous lessons we had made smaller, but functional iterations of this. However, as I was getting into the final parts of coding up the logic in Game class, I ran into an error:



<blockquote class="imgur-embed-pub" lang="en" data-id="t2Qg1Hw"><a href="//imgur.com/t2Qg1Hw"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

Infinite loop!? Why?! My tests were passing, so I was sure my syntax was correct. So I began to look through all of my methods to see what could be the cause of this.

After a couple hours of frustration debugging with pry, and some heated back-and-forth with my computer. I began to realize that my condition for the game being #over? was only checking to see if the board was full, not if it had been won, or a draw:

```
  def over?
    @board.full?
  end
```

Since checking if the board was full, would not fully cover every case of the came being finished early (won), or in the case of a draw, my method would just endlessly keep looping since the board was not 'full'.

I fixed my short-sighted code above to:

```
  def over?
    # checking ONLY #full? causes infinite loop in play method
    @board.full? || won? || draw?
  end
```

However, the infinite loop continued, much to my chagrin:

![To infinity and nowhere](https://imgur.com/a/GsSQD)

One redeeming quality of this still imperfect logic that I noticed was: the infinite loop was different, as well as the methods being called. Since there were less tests failing, I knew I was on to something. 

I began to see that my #draw? method, would check if the game was not won, and also #over?. Seems this did not quite cut it:

```
  def draw?
    !won? && over?
  end
```

After some more debugging, and many more threats of physical violence to my computer, I began to check the conditions that were being checked in my #over? method, that were not being checked in the dependent method in #draw? method.

Little did I know that if the board was not full, but #won?, it would cause an issue with my draw? method.

So I changed my #draw? method to:

```
def draw?
    !won? && @board.full?
end
```
 
Now, it would check to see if the game was NOT won AND full, in order to check if it was a draw.

My takeaways from this project:

1) Coding for many hours causes you to have visual fatigue. By that I mean, you begin to become desensitized to the spelling, and also behavior of your methods, especially if they are constantly interacting with eachother.
2) Coding Tic Tac Toe in full object orientation is not as easy even when you have previous work to build from.
3) I need to be more aware of the behavior of my logic, and not just syntax anymore.

I hope this helps someone in the future! 

Until next time...
