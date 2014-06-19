# Methods

Let's start with the line from above that appears simplest:

```ruby
1 + 2
```

I'm sure you can tell what this evaluates to just by looking at it, right? 1 + 2 = 3, boring. However, if you take a look at the other lines, you see one common feature that is absent from `1 + 2`: the mighty `.`, or dot. Go ahead and try this:

```ruby
1.+(2)
```

Same result. Why is that? In ruby, we use the `.` to call **methods** on an **object**. In Ruby, *everything* is an **object**, even things like numbers. So when we write `1.+(2)`, what we're really saying is "use the **+ method** on the **1 object** with **2 as the argument** used". This is the same as the following:

```ruby
1.send("+", 2)
```

In every case, we're simply sending the message `"+"` to the object `1` with the **argument** `2`. Thankfully, in order to make math in Ruby more intuitive, smarter Rubyists than I decided to make it easier to write basic arithmetic like we learned in school, so `1 + 2` works just as well as `1.+(2)`.

```ruby
# all three of these are equivalent
1 + 2
1.+(2)
1.send("+", 2)
```

----
