# Conditionals

We're getting closer to being able to actually do something useful with Ruby. Soon, we'll be building our first programs, so keep on chugging along, we're almost there!

The next thing we need to take a look at are **conditionals**. Most programming languages have some way to deal with what we call **control flow**, or the way that the path of the execution of a program is managed. Depending on some conditions, we often need to decide if we want to run one method or another. Let's take a look at an example:

```ruby
# in case you need it again
color_ary = ["red", "green", "blue", "cyan", "magenta", "yellow", "black"]

if color_ary.include?("red")
  puts "this array has my favorite color!"
else
  puts "ah man, this array lacks my favorite things"
end
```

<aside>When you see Ruby methods that end with a `?`, they are usually asking a yes or no question and will return either `true` or `false` depending on the answer. For this reason, they are called **boolean methods**.</aside>

Which one did you see happen? We used the `include?` method on our array which checks to see if the argument passed (in this case, "red"), is inside our array. Of course, our array does have "red", so the first `puts` is executed and the second one ignored.

Now go ahead and check to see if your own favorite color is part of `color_ary`. If not, what happened?

Now what about a failed condition?

```ruby
if color_ary.include?("beige")
  puts "gross! I hate beige"
else
  puts "I'm glad there is no stinkin' beige in here!"
end
```

This time, our first `puts` is ignored and only the second one shows up. This is the very nature of conditionals. It allows us to control the flow of our applications.

For a real-world example, think about when you use Facebook, Twitter or Gmail. **If** you are already logged in, it takes you to your homepage/inbox/whatever, **else** it takes you to the page where you can login.
Try using an if/else conditional on something else you know will fail. Pretty handy to have that `else` isn't it? You can even write something like the following if you'd like:

```ruby
magic_dog = nil
if magic_dog
  puts "wow, I didn't even set that variable"
else
  puts "oh, I definitely didn't"
end

if magic
  puts "this won't run"
else
  puts "and this won't either?!?"
end
```

What's going on there? If a variable is `nil` or `false`, it will fail the condition and drop down to the `else` clause. If you check a variable and it doesn't exist, it's `undefined` and will return a `NameError` instead of displaying anything. If we declared `magic_dog` as anything but `nil` or `false` and ran that conditional again, it should show the first line. Try this on your own now.

In Ruby, the only values that can fail a conditional are `nil` and `false` (but only when they aren't surrounded by quotes, as that would make them strings). Up above, `magic_dog` was `nil` since we had yet to define a variable by that name, so it failed the condition. If you had swapped out `magic_dog` for `false` or `nil`, it would also have failed. Now, if we had declared `magic_dog` as an empty string `""` or array `[]`, it would have actually passed since those values are not considered `nil` or `false` in Ruby.

Now what if you want to have multiple conditions? We can do that as well by using `elsif`:

```ruby
if color_ary.include?("pink")
  puts "wow, didn't expect pink in here!"
elsif color_ary.include?("magenta")
  puts "phew, at least we have magenta"
else
  puts "no pink, no magenta, I'm going home!"
end
```

We can also use the double-equal comparison:

```ruby
queen = "Elizabeth"

if queen == "Elizabeth"
  puts "God save the queen"
elsif queen == "Victoria"
  puts "She is not amused"
end

if queen != "Bloody Mary"
  puts "phew, dodged a bullet there"
end
```

On top of that, we can require multiple conditions to be true using `&&` (and) and check to see if one or the other conditions is true with `||` (or).

```ruby
his = "Jack"
hers = "Jill"
if his == "Jack" && hers == "Jill"
  print "Jack and Jill"
end

if his == "John" || hers == "Jill"
  print "one or the other"
end
```

----

## Exercise 4

Go ahead and write a couple of conditionals that use boolean comparisons (`==` or `!=`), `elsif`, as well as `&&` and `||`. Try to think about why you might want to use && instead of nested if conditionals (hint: which one might be less lines of code/less complicated).

----
