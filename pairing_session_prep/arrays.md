# Arrays


## An Array of Possibilities

Let's take a look at that last line again:

```ruby
"hello world, this is a humble programmer speaking".split
```

By calling the `split` method on the above string, we told Ruby to split the string into an array of strings, one for each word. By default, the `split` method will split a string into words by creating a new string each time it encounters a space character - thus, a new string item in the array for every word.

Arrays are a common **data structure** Rubyists use daily. Arrays are a way of storing many pieces of data as a collection, or list. We looked at strings in the last section, but what if you have a bunch of strings you want to group?

```ruby
# The employees of MakerSquare
"harsh"
"ravi"
"shaan"
"shehzan"
"mike"
"amanda"
"gilbert"
```

If we have a list of names like the one above, and we want to group them together to work with, we can use an array. In many programming languages, including Ruby, arrays use the square brackets, `[]`. We can make an array of the MakerSquare employees by putting those strings into square brackets like the following:

```ruby
["harsh", "ravi", "shaan", "shehzan", "mike", "amanda", "gilbert"]
["harsh", "ravi", "shaan", "shehzan", "mike", "amanda", "gilbert"].length
["harsh", "ravi", "shaan", "shehzan", "mike", "amanda", "gilbert"].sort
```

So there is our group of strings. Just like strings, we can still send methods to the array object to do something, like find the number of items in the array with `length` or sort the list of items alphabetically with `sort`. But before we go any farther, let's clean this up a little bit.

Typing out that entire array kind of sucks doesn't it? It probably seems like a major waste of time repeating yourself three times just to run a couple of simple methods on our array, and that is because it really *is* a waste of time. One of the most basic tools in the programmers arsenal is the **variable**, and it's meant to solve exactly this problem of repeating yourself.
