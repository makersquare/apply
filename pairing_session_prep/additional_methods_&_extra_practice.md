# Additional Methods & Extra Practice


## Other Useful Methods

There are a variety of other useful methods that Ruby comes with by default. We'll go through .each_with_index, .floor, .ceil, .shift and .unshift one by one so that you can add them to your toolbelt for use later.

----

## .each_with_index

[.each_with_index](http://ruby-doc.org/core-2.1.0/Enumerable.html#method-i-each_with_index) is a useful method for storing the indices of an array in a hash. For example, say we have an array:

```ruby
array = Array.new
array.push(1,2,3,4,5,6)
array       # => [1,2,3,4,5,6]
```

We can call .each_with_index on that array and give it two arguments, the item in question and its index. First, though, we'll create a new hash in which to restore the output of .each_with_index.

```ruby
hash = Hash.new
array.each_with_index { |item, index|
  # A block goes here
}
```

In the body of the block, we'll specifiy the manner in which we wish to save our information to hash.

```ruby
array.each_with_index { |item, index |
  hash[item] = index
}
```

Now, when we call hash, we will get a hash with our numbers in the array as keys and their indices as values.

```ruby
array.each_with_index { |item, index |
  hash[item] = index
}
hash  #=> { 1 => 0, 2 => 1, 3 => 2, 4 => 3, 5 => 4, 6 => 5 }
```

----

## Exercise #6

Given an array:

```ruby
array = ["Mike", "Gilbert", "Gene"]
```

Find the what index "Gilbert" lies in(Yes, the answer is obviously 1, but humor us and do it in code!).

----

## .floor and .ceil

Once you understand one of these methods, the other should be rather self-explanatory.

[.floor](http://www.ruby-doc.org/core-2.1.0/Float.html#method-i-floor) simply returns the largest integer that is less than or equal to the number that you pass in. This is a good way to round down a float.

```ruby
1.floor     #=> 1

1.2.floor   #=> 1
```
[.ceil](http://www.ruby-doc.org/core-2.1.0/Float.html#method-i-ceil) works in exactly the opposite way--you give it a float, and it returns the smallest integer greater or equal to what you gave to it.

```ruby
1.ceil    #=> 1
1.2.ceil  #=> 2
```

----

## .shift and .unshift

[.shift](http://www.ruby-doc.org/core-1.9.3/Array.html#method-i-shift) returns the first element of the array that it is called on and removes it from the array.

```ruby
array = Array.new
array.push(1, 2, 3, 4)
array.shift #=> 1
array       #=> [2, 3, 4]
```

If you give .shift an integer argument n, it will return the first n elements of the array.

```ruby
array           # Remember, this is now [2, 3, 4]
array.shift(2)  #=> [2, 3]
```

Now that you know how .shift works, how do you think [.unshift](http://www.ruby-doc.org/core-1.9.3/Array.html#method-i-unshift) works? Try it out in the console and see if you can divinate its meaning without consulting the docs or the next part of the lesson.

----

## .unshift

Did you figure it out?

Turns out, .shift and .unshift work rather differently. Whereas .shift takes elements out of an array, unshift actually *adds* elements to the beginning an array.

```ruby
array = Array.new
array.push(1, 2, 3, 4)
array.unshift(5)                   #=> [5, 1, 2, 3, 4]
array.unshift("arrays are cool!")  #=> ["arrays are cool!", 5, 1, 2, 3,4]
```

----

## Wrapping up

Phew, we made it! If you are still having any issues with these basics, don't worry. We're going to be focusing on ruby for a while, and we'll have plenty of time to reinforce the fundamentals. We're going to go ahead and do a few exercises now to practice what you've learned today. After that, there will be a few optional extensions if you'd like further practice.
