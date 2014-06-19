# Variables


## The Vide Vorld of Variables

```ruby
my_name = "Mike Ornellas"
my_name
my_name.downcase
mks_employees = ["harsh", "ravi", "shaan", "shehzan", "matt", "mike", "amanda", "gilbert"]
mks_employees
mks_employees.length
mks_employees.sort
sorted_mks_employees = mks_employees.sort
```

We can use variables to assign a name to an object. Just like in algebra, the value of a variable can change over time. I can make a variable that is set to a string (like `my_name` above), or I can store an array in a variable. Heck, we can even store the result of a method in a new variable like we did with `sorted_mks_employees` up above. In Ruby, we set variables by setting a name equal to something. Unlike strings, these names aren't surrounded by quotation marks - if they were, they would be strings!

```ruby
name = "Jim"
"name"
name
name = 2
name
```

 Variables are assigned a value with the `=` method:

```ruby
empty_array = []
empty_array << "not so empty anymore"
empty_array.push("this is just getting ridiculous")
not_empty_array = empty_array
empty_array.pop
empty_array
not_empty_array
```

In line 1, we set a variable `empty_array` to an empty array by setting it to `[]` and then added items to the end using either the `push` method or by using the `<<` (shovel) operator to shove something onto the end of the array. Likewise, we can `pop` things off the end of the array using the `pop` method which will remove the last item from the array. You can kind of think of `pop` as taking a chip out of the pringles can, `push` is putting it back in.

----

Using variables, we also get another neat tool to use: string interpolation, which is a fancy phrase for something relatively simple.

```ruby
name = "Mike"
'Hello, my name is ' + name + ', and I am a Ruby developer'
"Hello, my name is #{name}, and I am a Ruby developer"
```

Both lines should print out the same exact thing, but it's much more common for Rubyists to use the second form with `#{}` instead. There is one caveat though:

```ruby
'Hello, my name is #{name}, and I am a Ruby developer'
```

Not what you expected right? This has to do with the difference between single-quote strings and double-quote strings. Single-quoted strings don't allow for string interpolation, while double-quoted strings do allow interpolation.

----

## Exercise 1

We talked about using `puts` to print strings to the screen, but did you know you could also get input from users? Try `user_input = gets.chomp` in IRB and then look at the `user_input` variable to see what is stored. Try doing it without `.chomp` and see what changes.

----

## Acessing Array Items

In Ruby, you can grab items from an array by their *position*. So, for example:

```ruby
color_ary = ["red", "green", "blue", "cyan", "magenta", "yellow", "black"]
color_ary[0]
color_ary[1]
color_ary[2]
color_ary[-1]
```

Again, this is kind of strange, right? Why do we start at 0 instead of 1? You can think of it like a number line that starts at 0 and goes to 10. The first point on the line would be at 0, the second point at 1, and so on. Arrays work the same way, except we call each point an `index`, so if we want the first thing in an array, we look at index 0, if we want the second, we look at index 1, and so on.

A crucial aspect of arrays is that you can grab any value from an array based on its position. So, in this example, `color_ary[0]` grabs the first item in the array (the string "red"), `color_ary[1]` grabs the second item, and so on. We can also go backwards using negative numbers with the last item being at index `-1` and the second-to-last item being at index `-2` (like we did above).
We even have some convenient methods to make this a little easier to remember:

```ruby
color_ary.first
color_ary.last
```
----

## Exercise 2

Can we have both strings and integers in an array? Can you put arrays in arrays? If you can **nest** arrays like that, how do you access an item in a nested array?

```ruby
array = [0, 1, 2, [0, 1, 2] ]
array[3]
array[3][0]
```
