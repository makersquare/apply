# Ruby Classes

# Class is in session!

<aside>
  Remember that if you already feel comfortable with this material, you can skim through it and move onto the next lesson. **This lesson has more new material than the previous.**
</aside>

You've done a lot of work with Ruby and that's great! Forget everything you've learned.

Just kidding. We'll be using quite a few of the concepts you've learned from the past lessons, but keep an open mind because we're about to dive into the fundamentals of Ruby.

Today we're going to learn about Object-Orientation in Ruby. Specifically, you'll be learning the following:

* What an object is (at least in Ruby terms)
* How to use methods to send messages to objects
* How to use classes to make new objects

We'll start off with this high quality video with state-of-the-art animation:

<iframe width="620" height="315" src="http://www.youtube.com/embed/c5kfCH50wl0" frameborder="0" allowfullscreen></iframe>

----

## Everything is an object

That was a pretty old school video, but it was packed with a lot of information that's crucial for what we're doing today.

Every piece of data you've seen and worked with - they're all objects. That includes all of these:

```rb
:wuddup     # Symbols
"Hello"     # Strings
42          # Integers
3.14        # Floats
[1,2,3]     # Arrays
{ x: 'y' }  # Hash
```

Remember that in Ruby, when we pass methods to objects, we are really using .send to "send" it a message. But there's a shortcut out there that you may know of. When you send an object a message, the first part of the message is always telling it what to do. In the examples above we told the objects to `add`, `reverse`, `split` and `join`. The rest of the message always varied.

To make message passing easy, you can take the action out of the message and replace send with that action.

`"hello".send(:reverse)` becomes `"hello".reverse`

----

## Exercise #1

Translate the following into the new format and make sure you get the same results:

```ruby
{ ruby: 'backend', html: 'frontend' }.send(:invert)
10.send(:/, 3)
['a', 'b', 'c', 'd'].send(:slice, 1, 2)
```

----

## Everything is an object!

As we said before, everything that you work with in Ruby is an object and every action that you take is a method. Breaking down this example:

```ruby
['a', 'b', 'c', 'd'].send(:slice, 1, 2)
```

* The array in question is an object
* `send` is the method you're performing on the object
* `:slice`, `1`, and `2` are each objects - they are called **arguments**. Arguments are pieces of additional data being sent to the object for it to perform the task.
* The final object in this example is the response of the method call. Every method will respond with some object or another, in this case it's `["b", "c"]`

In the new format, the method is now `slice` instead of `send` and the arguments are just `1` and `2`.

All objects have a *class* associated with them. Classes determine the structure of the object you're looking at and what methods you can call on it.

Call the **class** method on the following objects:

```ruby
"hello"
42
72.2
:apple
[1, 2, 3]
{a: "b"}
```

As a response, you'll get the name of it's class. Knowing the class helps you figure out what methods you can and can't use on the object. You can go to [Ruby Docs](http://ruby-doc.org/), or use the [Dash app](https://itunes.apple.com/us/app/dash-docs-snippets/id458034879?mt=12) if you're on a Mac, and search for the class name to find a list of methods available along with documentation. Look up `Array` and check out a new method or two.

----

## The Real Way to Create Objects

Ruby gives you a few objects right off the bat, so that you're not left wandering alone into emptiness. The subset we're going to look at are the classes that are given. Yes, even classes are objects... everything is an object. (No really. You can even check the class of a class.)

Here are a few of the classes given to you:

```ruby
String
Symbol
FixNum
Array
Hash
Float
```

There are more, but these are a few that are familiar to you. These are objects of the type *Class* which gives them the ability to use a method called *new*.

A class is essentially a template or a factory that tells you what kinds of objects it can create, and using the `new` method, the factory produces the object. For example:

```ruby
Array.new
Hash.new
```

The objects that these return are **instances** of the classes `Array` and `Hash` respectively. The array factory will give us an array and the hash factory will do the same.

However, this is quite pointless unless you label the instance that this returns. You label an object by picking a name and equating it to the object:

```ruby
my_special_array = Array.new
```

The whole concept of **variables** is based on labeling objects in order to reuse them.

Very cool. Now we know about how method calls really work, how objects are truly created at the root and the general idea of classes. All of this was a precursor for us to be able to... *drumroll*... create our own classes!

----
##Breather Time!

Let's put some thoughts together

1. Everything in Ruby is an object
2. All objects have classes
3. Classes are objects too
4. Classes have the class, `Class`
5. We can create an instance of a particular class by using the new method

Seems like we're trying to create an instance of the class Class. (Insert xzibit meme here)

Yeah... I'm confused, too. We'll go through an example together. First, we'll learn to run a Ruby program through a text file rather than in IRB.


Open up Sublime Text and create a new file and save it as `class.rb` on the desktop.

In terminal, navigate to the desktop and type the command `ruby class.rb`.

This will execute all of the Ruby code in the file `class.rb`. This is an easier way to run code so that we don't have to rewrite our code in IRB every single time. Nothing will happen right now because we haven't written any code.

In `class.rb`, type `1.+(7)` and save. In the terminal run the command `ruby class.rb` again.

Still nothing. That's because executing a method does not print anything to the screen. IRB prints out the result of the method execution because it's meant to be used as a tool to help you code, but in regular execution, the code will NOT be printed unless you tell it to.

One of the objects we didn't mention earlier is `Kernel`. `Kernel` is the computer system and you can do interesting things to it like print to the screen. You may or may not have already been doing this...

In `class.rb` type `Kernel.puts("Hello World")`. Run the Ruby code in terminal again and watch the magic work.

<aside>Note that we've been using the `puts` statement without using the `Kernel`. It works because, in Ruby, `Kernel` is the **implicit receiver** of any message not called on a particular object.</aside>

Great! Now that we are safe from rewriting our code a million times we can start creating classes. To create a class we create an **instance** of `Class`.

```ruby
Pet = Class.new # put this in your class.rb file
```

Bam! We got ourselves a new class! Congrats!

----
## Harnessing OOP

So...what can we do now? You can create a new `Pet` now since the class `Pet` exists now. Try adding this to the end of your `class.rb` file:

```ruby
dog = Pet.new
Kernel.puts(dog)
```

Run the Ruby code and check out the results. We've created an instance of a Pet.

Pat yourself on the back!

----

## One More Way to Run Ruby Code!

Within terminal, instead of running `ruby class.rb`, we can get the code working in IRB.

* Jump into IRB
* Type in `load 'class.rb'`
* Type `dog = Pet.new`
* Type `Kernel.puts(dog)`

`load 'class.rb'` loads all class and method definitions into your IRB session, so you can interact with them on the spot.

Remember that you have to load the Ruby file everytime you change it. It won't pick up the new changes automatically.

----

## Back to Class

Back to the Pet class. Unfortunately, you can't do much with this pet object. For example, try creating a new dog in your IRB session and making the dog bark by typing the line `dog.speak` in your IRB session.

Yeah, Ruby just exploded. Actually, Ruby gave you a super helpful error message.

```ruby
NoMethodError: undefined method `speak' for #<Pet:0x007fa1198b6228>
```

When you read this error message, you can see that it's complaining, because you don't have the method `speak` defined. The message is pretty much saying:

```ruby
This method is not defined. The Pet class doesn't have a method speak defined for it
```

Sounds like we should define this method! Add the following code to the class definition. **Type it. Don't copy it. You'll understand it better by typing it out.**

```ruby
Pet = Class.new do
  def speak
    Kernel.puts("Woof Woof")
  end
end

# in IRB
load 'class.rb'
dog = Pet.new
dog.speak
```

Using the **do end block** we added a new functionality for the Pet class so that it can speak. Note the anatomy of a method definition:

1. The block of code is surrounded by `def` and `end`
2. `def` is followed by the method name, in this case `speak`
3. Next to the method name, in parantheses you can list the arguments that you pass in. We've passed in 0 arguments this time, so the parantheses are actually optional.
4. The lines of code between `def` and `end` are indented over and is the code that's run when you call the method.

----
##Adding Arguments

Write 2 other methods that a `Pet` can use. Both methods must use an **argument**. Use Google to help you out. It will look similar to something below:

```ruby
def your_age(years)
  puts "You are only #{years} years old?! You child."
end
```

Try out the methods in IRB.

You've just created your first class with 3 methods. Awesome!

Now create a class of your own with 2 methods of your choice.

<div class="deliverable">
  You should now have defined two different classes (`Pet` and one of your choice). Each one of the classes should have various methods that take arguments.
</div>

----

##Refactoring

Let's reorganize this using some ruby shortcuts!

Instead of typing:

```ruby
Pet = Class.new do
  ...
  ...
end
```

Ruby let's you make that look slightly cleaner and simply type:

```ruby
class Pet
  ...
  ...
end
```

Go ahead and convert the code for the Pet class and your own class.

----

## Instance Variables

Classes allow you to have **instance variables**. If we have a class `Cat`, instances of that class represent individual cats, and instance variables are the properties (`height`, `weight`, `name`) that describe that cat.

Comment out the current code in `class.rb`. You can do this highlighting the code and hitting `command + /`.

Write the following code in the `class.rb` file:

```ruby
# class.rb
class Marker
  def set_color(my_color)
    @color = my_color
  end

  def write
    Kernel.puts("I am writing with a #{@color} marker!")
  end
end
```

See what is returned after executing the following in IRB code. Don't forget to `load class.rb` in IRB.

```ruby
#IRB code
red_marker = Marker.new
green_marker = Marker.new
red_marker.set_color("red")
green_marker.set_color("green")
red_marker.write
green_marker.write
```

Whoa there! That's quite a bit of code. Let's break it down.

In the `set_color` method, we assign the input `my_color` to the variable `@color`. Because of the `@` sign, Ruby recognizes that it's an instance variable. The variable is tied with just the instance of `Marker` that calls the method `set_color`.

When we create instances of the `Marker` class, we call `set_color` with both `Markers` using different colors. When we call the write method on each `Marker`, they print out different messages based on the color set.

<aside>While you can use instance variables in any method within the class, you cannot do the same with regular variables.</aside>

----

## Exercise #3

Now go back to the `Pet` class, allow a user to set what kind of noise the pet makes and when the pet speaks, have it make that sound.

----

## Exercise #4

For the class you created, think of a use for an instance variable and implement it.

Also, think of 3 other use cases for instance variables. No need to implement!

----

## Extensions

Convert the following methods to use the **send** method. Put your results in `class.rb`

```ruby
5 * 5
"omg".upcase
['a', 'b', 'c'].at(1)
['a', 'b', 'c'].insert(2, 'o', 'h', 'n', 'o')
{}.size
{character: "Mario"}.has_key?(:character)
```

Convert the following methods to not use the `send` method. Put these results in `class.rb`

```ruby
6.send(:-, 32)
{html: true, json: false}.send(:keys)
"MakerSquare".send(:*, 6)
"MakerSquare".send(:split, 'a')
['alpha', 'beta'].send(:[], 3)
```

----

### Using Git

If you've gone through Git lessons/tutorials then run through this step. It's not required as part of the technical interview prep, but it's useful to know.

* Go to [github.com](http://www.github.com).
* After signing in, click on the icon next to your user name at the top right of your screen. (On hover it will say 'Create a new repo').
* Name your repo "ruby_classes-1".
* Under quick setup, click on "http" and copy the link.
* In terminal, go to a directory where you want to save your work.
* Type the following code in terminal:

```console
mkdir ruby_classes-1
cd ruby_classes-1
touch class.rb
git init
git add .
git commit -m "Initial commit"
git remote add origin ((paste your git url here))
git push origin master
```

These are basic steps you run in order to get a git repo started.

Here's a refresher on the Git process that you see above.
*  `git init` - initiating "git" on your local computer
*  `git add .` - adding any changes you made to "staging"
*  `git commit -m "Initial commit"` - committing everything that is staged
*  `git remote add origin <url>`... - adding the ability to push your local directory to your personal remote from github.com
*  `git push origin master` - pushing your local directory to your Github repo

----

## Glossary

<dl>
  <dt>Ruby object</dt>
  <dd>An instance of a Ruby class with methods inherited from the class and its own instance variables to store information in</dd>

  <dt>class</dt>
  <dd>A "blueprint" for Ruby objects that provides a set of methods and the names of instance variables that can be used and set to make unique objects</dd>

  <dt>method</dt>
  <dd>A message we send to Ruby objects in order to do something</dd>

  <dt>instance variable</dt>
  <dd>Bits of unique information that you can store in each object (e.g. @name on an instance of a Dog class)</dd>
</dl>
