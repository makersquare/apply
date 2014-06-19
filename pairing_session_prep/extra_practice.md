# Extra Practice


## Additional Exercises

We briefly looked at Symbols as keys in hashes, but we didn't really go into what they were. Symbols are similar to strings but slightly different. Instead of trying to explain, I'd rather show you. Open up IRB and create two different variables containing the same string (e.g. `a = "hello"` and `b = "hello"`) and then two variables containing the same symbol (e.g. `c = :yes` and `d = :yes`). Now, try using the `object_id` method on each of your variables. Anything surprising? If we use up some of our computer memory everytime we make a new object, what do you think would use more memory, 1000 variables containing the same string or 1000 variables containing the same symbol?

----

When should you use an array vs. a hash? With a dictionary, you don't care what order things are in, you just want to see the definition of the word you are looking up (like seeing the value of a key you are looking up). Try making a simple 5 word dictionary using a hash, with the words as keys and the definitions as values. Now, try to make something with an array that wouldn't make sense as a hash. Think about how its ordered and how it operates kind of like a stack of cards.

----

Try making a few more complicated if/else conditions (like if/else conditions nested inside of if/else conditions), think about how easy (or hard) it might be to reason your way through more complicated conditionals. Try making a few if/else conditionals that will always fail. Try making some that use `&&` or `||` to add more conditions.

----

## Extensions (optional practice)

Using modulo, `&&`, conditions, loops and the following range `(1..100)`, create a loop that puts "FizzBuzz" if the number is divisible by both 3 and 5, "Fizz" if the number is divisible by only 3, "Buzz" if the number is divisible by only 5, and the number itself if not divisible by 3 or 5.

----

Using conditionals, variables, `gets` and `puts`, make a choose-your-own-adventure game! In these types of games, you give a user a couple of options to proceed, they pick one and either die/lose, or continue to proceed on. Try to make it extra spooky for maximum corniness points.

----

If you're interested in stretching your mind, check out [Project Euler](http://projecteuler.net/problems). Don't be intimidated by the math, you can search for ways to solve a lot of these problems and then try to figure out the best way to do so in Ruby. Be patient, be willing to Google away to figure out problems and try not to get intimidated!

Go ahead and start a new git repository for your solutions to live in. Here are a few of our favorite problems to get you started:

* [Multiples of 3 and 5](http://projecteuler.net/problem=1)
* [Largest product in a series](http://projecteuler.net/problem=8)
* [Counting Sundays](http://projecteuler.net/problem=19)
* [Sum square difference](http://projecteuler.net/problem=6)
* [Even Fibonacci Numbers](http://projecteuler.net/problem=2)
* [Currency Challenge](http://projecteuler.net/problem=31)

----

We saw some methods today, but there are tons we didn't get a chance to look at. Check out the official API (Application Programming Interface) documents for [Strings](http://www.ruby-doc.org/core-2.0/String.html), [Arrays](http://www.ruby-doc.org/core-2.0/Array.html), [Hashes](http://www.ruby-doc.org/core-2.0/Hash.html) to see the methods we have available. If you see one you want to check out, try it out in IRB. If you find the documentation confusing, you can always search for the name of the method to see if other people have had similar questions.
