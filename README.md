# Enumeration and Iteration

![Picasso on Abstraction](http://ironboard-curriculum-content.s3.amazonaws.com/web-development/abstraction-bull.jpg)

_Picasso on Abstraction_

_Notice that the details of the bull are removed and the image is still identifiably a bull_

## Objectives
1. Understand the concept of iteration 
2. Understand simple iteration or looping
3. Get an introduction to complex iteration

## Iteration vs. Looping

We've already covered basic looping and you can refresh your memory [here](https://github.com/learn-co-curriculum/simple-loops). Now that you're all brushed up on simple looping, let's discuss the difference between looping and a new concept––iteration. **Looping** occurs when you tell your program to do something a certain number of times. **Iteration** occurs when you have a collection of data (for example, an array), and you operate on each member of that collection. 

For example, if I tell my program to print out the phrase "I love programming" 5 times, that's a loop. If I tell my program to enumerate over the array `[1, 2, 3, 4, 5]` and add 10 to each number, that's iteration. 


## `loop` - The Least Abstract

Let's talk about the algorithm required to go through all the individual items in a set.

Imagine having a basket with 10 apples in it. What would you need to do to make sure you took out all the apples?

You might think that it's enough to say take an apple out of the basket one at a time. But that's not entirely true, because at a certain point, there are no more apples in the basket, and you need to know that, or else you'd keep on reaching in for more apples. So the algorithm is a bit more complex. It might look like this:

1. Keep track of how many apples there are in the basket.
2. Keep track of how many apples you have taken out of the basket.
3. Start a loop.
4. If the amount of apples you take out is less then the amount of apples in the basket, take one out and increment the amount of apples you've taken out by one.
5. If the amount of apples you take out is greater then or equal to the amount of apples in the basket (also known as less then the amount), break out of the loop.

This will ensure that we take out all the apples and never reach into the bucket when there are no apples left.

In ruby, we might implement this most basic algorithm in the following manner.

```ruby
basket = ["apple 1","apple 2","apple 3","apple 4","apple 5","apple 6","apple 7","apple 8","apple 9","apple 10"]

apples_in_basket = basket.size # Step 1
apples_taken_out = 0 # Step 2

loop do # Step 3
    if apples_taken_out < apples_in_basket 
        # Step 4
        puts "Taking out #{basket[apples_taken_out]}"
        apples_taken_out += 1
    else
        # Step 5
        break
    end
end
```

So that's the least abstract implementation of the algorithm. All the details are there, every step is accounted for explicitly in the code. We won't change the algorithm, we'll just look at more abstract implementations.

## `while` - A Little More Abstract

The goal of abstraction is to remove details.

```ruby
basket = ["apple 1","apple 2","apple 3","apple 4","apple 5","apple 6","apple 7","apple 8","apple 9","apple 10"]

apples_in_basket = basket.size # Step 1
apples_taken_out = 0 # Step 2

# Step 3 + 4
while apples_taken_out < apples_in_basket
    puts "Taking out #{basket[apples_taken_out]}"
    apples_taken_out += 1
end
```

What we did here was first combine step 3 and 4, initializing our loop based on a condition, which is exactly what the word `while`, both in code and in english, means, it is a conditional loop. Abstraction didn't make our code less clear, it in fact made our code absolutely precise. Brevity for the sake of brevity is silly, our is to always express ourselves as clearly and honestly as possible. Because our loop is conditional from the start, by using the while loop mechanism, we don't need to explicitly break out of it, making step 5 implicit.

## `each` - The Most Abstract

> "Being abstract is something profoundly different from being vague... The purpose of abstraction is not to be vague, but to create a new semantic level in which one can be absolutely precise." Edsger Dijkstra

```ruby
basket = ["apple 1","apple 2","apple 3","apple 4","apple 5","apple 6","apple 7","apple 8","apple 9","apple 10"]

# Step 1,2,3,4,5
basket.each do |apple|
    puts "Taking out #{apple}"
end
```

Here we see the full power of the ruby iterators. As Kent Beck says, "You don't use 3-4 lines to express iteration, you use one word." If you mean each apple, just say each apple. All the details of the algorithm are removed and replaced with the intention of our code, not the implementation of the algorithm.
