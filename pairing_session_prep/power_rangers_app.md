# Power Rangers App

# Go Go Power Rangers!


In this lesson, you will practice testing while reviewing previous concepts:

* Inheritance.
* Passing objects into methods.

You will also learn about `Modules` and `Mixins`.

First we'll need to create the project locally

* Fork the PowerRangers repository from [here](https://github.com/makersquare/powerrangers)
* Clone it down to your own local directory
* Open up `powerrangers.rb` in Sublime Text

That's right! We're building power rangers from scratch. We're starting off with a Person and building our way up.

----

## Testing Before each step

Write your test before writing your code each step of the way. It's a different process from what you're used to and will get you good practice with the red, green, refactor flow of test driven development.

Reference previous lessons to create the right file structure for your directory and Gemfile.

----
## Making People

Create the class `Person`.

* A person has attributes: `name` and `caffeine level`. `caffeine_level` should be an integer value representing how caffeinated a person object is.
* A person can `run`, `scream` and `drink_coffee`
* `drink_coffee` would increment the `caffeine_level`

You can be creative with exactly how these methods are implemented. For example, the `scream` method can be a puts statement that renders a scream. `drink_coffee` can increase caffeine level as much as you see fit.

Create your tests first. Start with a test for instantiating a Person object, get it to pass then create tests for other functionality before adding them to your application.

Remember to commit your code.

----

## Making Power Rangers

Create the class `PowerRanger` which extends (inherits from) `Person`

* A `PowerRanger` has attributes: `strength`, `color`
* A `PowerRanger` can `punch` and `rest`
* Punch takes **another person as an argument**. A person that is punched should scream and run away (this can be a puts statement). If the punch strength is greater than 5, he/she should be somersaulted into the air. This will decrease your caffeine level for sure.
* Punching takes a lot energy/caffeine out of you. Decrease caffeine when you punch.
* Create a class method called use_megazord which does the same thing as punch but with a strength of 5000! Be creative with what it does.

----

## Enemies Have Arrived!

Create a class EvilNinja which extends Person

* An EvilNinja has attributes: strength and evilness
* An EvilNinja can punch and cause_mayhem
* Punch works the same way as for PowerRangers
* Cause_mayhem takes a person as an argument and drains their caffeine level to 0. **Terrifying**

Create a method called fight scene where you have 2 PowerRangers, 2 EvilNinjas and 2 Persons enact a scene and use their methods at least once.

Remember a method doesn't have to be inside a class to be used.

----

## Modules and Mixins:

See a problem? We have some redundant code here my friends. The method `fight` is used in both EvilNinja and PowerRanger, but we just copy + pasted the code for it.

We may even have future classes such as `TrainedMonkey` that can fight as well. **DRY code** = Don't Repeat Your code. We can't use inheritance and put the code in Person because not all people can fight.

Ideally we want PowerRangers and EvilNinjas to inherit from a 2nd class. Ruby has a workaround using **Modules/Mixins**

Read up on `Modules` and `Mixins` at this link from [TutorialsPoint](http://www.tutorialspoint.com/ruby/ruby_modules.htm). We'll give you a general idea of what `Mixins` are below but TutorialsPoint gives a more in depth explanation of Modules and Mixins.

----

## Using Modules as Mixins

One use of `Modules` is to mix in bits of code and methods. This is useful for code that gets repeated often. In the example below, instead of writing the `roar` method twice and putting it in class Tiger and Lion, we put it in a module called `Warn`. The code in the module Warn can then be added by using the keyword `include`:

```ruby
module Warn
  def roar
    puts "ROAR!"
  end
end

class Cat
  def purr
    puts 'meow'
  end
end

class Tiger < Cat
  include Warn
end

class Lion < Cat
  include Warn
end

class Kitten < Cat
end

```

Now the `Tiger` and `Lion` both have the method `roar`. You check that out by first running the code above in IRB along with this code block:

```ruby
t = Tiger.new
t.roar
l = Lion.new
l.roar
```

Modules when used this way are also referred to as `Mixins` because you are mixing in code.

Mixins make up for the fact that ruby doesn't allow multiple inheritance. That is, ruby classes can only inherit from one other class. For example you can't do something like this: `class Tiger < Cat < Animal; end`.

Mixins are also helpful in cases where you don't want to include a method in all cases - the `Kitten` class in the example above doesn't need the method `roar` so we didn't mix it in.

Use `Modules` and `Mixins` to make your code DRY.

###Let's wrap this up!

* Make sure your method `fight_scene` still works!
* Commit your code.
* Push your code to GitHub

----

## Extensions

You'll be creating a messaging system. The basic classes you need to create are Email, PreferredEmail, SnailMail, and SMS. Like with the Power Rangers exercise, you can be creative with how the classes and methods implemented. Write tests before you write your code.

You're required to use the concepts of inheritance and Modules/Mixins.

Create a system of these objects that interact with each other.

Come up with your own system of objects that require inheritance and/or Modules/Mixins and implement it.
