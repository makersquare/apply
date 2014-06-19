# Loops
## Getting Loopy

Not only can we grab individual objects out of an array by their position, we can also perform operations on all the elements of an array in sequence. If you've ever used other programming languages, you might be familiar with a scary-looking creature called the **for loop**. Ruby has loops too, but we usually use the much friendlier `.each` method:

```ruby
color_ary.each { |color| puts color.capitalize }
```

We're still using methods here, like we've done before, but the arguments look different than what we've encountered so far. Let's break it down a bit. We have our trusty old `color_ary` from before, and we're calling the `each` method on it. The `each` method works by going through the array, item by item, and running the code specified for each item. We specify the code to run for each item using what we call **blocks**, which you can recognize by the curly brackets (`{}`) and vertical pipes (`|blah|`).

The `each` method will loop through each item in the array and run the specified code in the block. The `| |` contains the **block argument** you use in your block's code for the items that are being looped through. This argument can be named anything you like, so for instance, the following are both exactly the same:

```ruby
[1, 2, 3, 4, 5].each { |n| puts n }
[1, 2, 3, 4, 5].each { |number| puts number }
```
----

We can do more than one operation in a single block with `each` as well:

```ruby
color_ary.each do |x|
  puts x.reverse
  puts x.upcase
end
```

You may have noticed that we used do/end this time rather than {}. Both work exactly the same, but its usually considered proper for Rubyists to use curly brackets when the block fits on one line, and use do/end with multi-line blocks.

Now let's try writing a multi-line block using do/end. Go ahead and use `color_ary` and some string methods we have already seen like `upcase`, `downcase` or `reverse`. After that, let's try something a little more difficult:

```ruby
new_array = []
[1, 2, 3, 4, 5].each { |num| new_array << num ** 2 }
new_array
```

So, what did we do here? We created a new, empty array, looped through an array of numbers 1-5 and then took the square of each number in the array and inserted it into the new array. Pretty cool, but there is a way to cut out the new array step:

```ruby
newer_array = [1, 2, 3, 4, 5].collect { |n| n ** 2 }
```

`collect` loops through the array (just like `each` did), performs the block operation, just like `each` did, but then returns the results as a new array. Try it yourself with the following array and the `capitalize` method:

`presidents = ["barack", "george", "bill"]`

Pretty neat, right? We accomplish the same thing we did with `new_array` above, but in one line instead of three. Less code means less chance for typos, less chance for bugs, and (usually) less chance for confusion, so you can *probably* guess which style I prefer.

We also have ranges, which are kind of like arrays but represent an **interval**.

```ruby
(1..5).each { |n| puts n }
(1..5).to_a
(1..5).to_s
(1...5).to_a
```

There are two types of ranges: ranges with two dots include all the values listed (inclusive), while three dots excludes the last number (exclusive). Ranges can be an easy way to create ordered arrays of numbers to loop through, like we did on the first line.

Try making a range from 1 through 25 end then print out only the even numbers (hint: remember modulo).

----

## Exercise 3

Create an array of numbers and use `each` to loop through them and print them to the screen using puts. When you've finished that, try using `each` to loop through an array of strings and call one of the string methods we learned on each string (like `upcase`).

----

## Comparing Values

In Ruby, we also have a way to compare a value to something else:

```ruby
first_value = 12
second_value = 13
third_value = 13

first_value == 12
second_value == first_value
second_value == third_value
third_value == 12

first_value != second_value
second_value != third_value
```

In Ruby (and many other languages), we use the `==`, or double-equals, operator to compare values. If they are the same, it returns `true`, if they are different, it returns `false`. We also have a not-equal operator: `!=`, which checks to see if the values are **not** the same.

Try comparing some values of your own and see what comes up. Not too surprising, eh?
