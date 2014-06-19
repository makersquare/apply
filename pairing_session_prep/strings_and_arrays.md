# Strings and Arrays


## Untying strings

```ruby
"I'm a string"
'I too am a string'
"usa".upcase
```

Here we have a **string**, or a line of text set off by quotation marks. Strings are always surrounded by single or double quotes. All string objects have built-in methods we can use: `upcase` is one. Unlike the `+` method we used with the numbers above, we don't have to pass any **arguments** along for it to work. We can just take any string and send it the upcase method as a message, and it will capitalize all the letters in the string. Try each of the following in IRB:

```ruby
"USA".downcase
"mike".capitalize
"stressed".reverse
"flower".length
"hello world, this is a humble programmer speaking".split
```

Again, like before, each time we have a string object that we send a **method** to using our pal `.`. So far, all of the methods we've used came with Ruby, but soon you'll be able to craft your own methods to do whatever you'd like.

Now, what about outputting some **strings** to the terminal? We actually have two methods to do this:

```ruby
print "hello"; print " world"
puts "hello"; puts "world"
```

Can you spot the difference? `puts` inserts a new line at the end of the string while print does not.

<aside>The semicolon allows us to put two statements in a single line of code, normally you won't want to do that, but for the sake of illustrating print vs puts, we used it here.</aside>
