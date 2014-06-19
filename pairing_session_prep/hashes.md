# Hashes

## Hash it out

So we've looked at arrays already, but arrays have a weird step-brother called hashes. Let's look at an example:

```ruby
font_options = { :size => 12, :font_family => "Times New Roman" }
font_options.length
```

With hashes, we store collections of objects, just like we did with Arrays earlier. Unlike arrays, which stored objects in order (like `color_ary[0]`, `color_ary[1]`, etc.), Hashes store objects as **values** stored at a named **key**. In our hash above, `:size` and `:font_family` are keys, and `12` and `"Times New Roman"` are values stored at the respective keys. Keys are usually `symbols`, which start with a colon (`:`).

The values are specified with something we call the **hashrocket** that looks like `=>`. There is also a newer syntax as of Ruby version 1.9 that looks like `size: 12, font_family: "Times New Roman"` but there are certain situations where that syntax can make methods confusing, especially when we get to Rails, so let's stick with the hashrocket syntax, at least for now.

Go ahead and make a hash called `abbr` that stores 5 abbreviations, with the abbreviation themselves set as the keys and the phrase being abbreviated set as the values (e.g. "NSA" : "National Security Agency").

We can also loop through hashes, just like we did with Arrays earlier:

```ruby
font_options.each do |key, value|
  puts key.to_s + ":"
  puts value
end
```

<aside>Why do you think we had to call `to_s` on `key`? Try it without the to_s and read the error message carefully, feel free to grab me if you still can't figure it out</aside>

Notice that, unlike arrays, we need to pass an argument for both the key and the value when looping through a hash.

----

## Exercise 6

Go ahead and loop through your abbr hash and print out the keys and values in an attractive way.
