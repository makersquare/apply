# Cookbook App
# Building Ruby applications from scratch

Building fresh applications is hard. Even experienced developers often struggle with it. Sometimes, it can even feel easier to have a very poorly-coded app dropped in your lap to be fixed than to figure out a new solution out of thin air.

For this lesson, we'll guide you through building a `Cookbook` application step by step. It'll prepare you to build a similar application almost from scratch. We're going to quickly implement a simple Cookbook that can hold Recipes and has instance variables, initialize methods, attr_accessors and interaction between classes.

Remember to make a commit after finishing any method or piece of code you're working on. Try to make your commit messages informative about what you did.

**Good**:
"Implemented the add_recipe method that adds recipes to instances of the Cookbook class"

**Bad**:
"added some stuff"

----

## Ensuring your code works

We'll be writing our code in a .rb file using Sublime Text. In your `code` directory or directory of your choice, create a `cookbook.rb` file.

We'll be giving you test code that will guide you toward building your Cookbook app. Your job is to make the chunks of test code functional by building out the appropriate method and classes.

<aside>Whenever there is an expected output for a piece of code, it'll be placed as a comment either next to the code or on the next line of the code.
</aside>

----
## Creating our classes and initialize methods

Here is the first chunk of code you need to make functional:

```ruby
mex_cuisine = Cookbook.new("Mexican Cooking")

burrito = Recipe.new("Bean Burrito", ["tortilla", "bean"], ["heat beans", "place beans in tortilla", "roll up"])

```

As you can see it requires two classes - `Cookbook` and `Recipe`.

Create those classes in your `cookbook.rb` file.

Add the initialize method for the `Cookbook` class and set its parameter to `title`. The `Cookbook` class should look like this after you're done:

```ruby
class Cookbook
  def initialize(title)
    @title = title
  end
end
```

For the `Recipe` class, create the initialize method and set the parameters as `title`, `ingredients`, and `steps`.

Check out your work in IRB. Remember this means running `load "cookbook.rb"` while inside IRB. There you can copy and paste the entire test code we gave to make sure it works.

You'll need to exit and re-enter IRB to load `cookbook.rb` and run your test code as you go along. This is to prevent IRB from creating unintended errors as it holds onto previously run code in its memory.

----

## Creating getter methods

We're adding more test code to what we have above. You will be creating methods so that the added code from lines 4 and onward work:

```ruby
mex_cuisine = Cookbook.new("Mexican Cooking")
burrito = Recipe.new("Bean Burrito", ["tortilla", "bean"], ["heat beans", "place beans in tortilla", "roll up"])

puts mex_cuisine.title # Mexican Cooking
puts burrito.title # Bean Burrito
p burrito.ingredients # ["tortilla", "bean", "cheese"]
p burrito.steps # ["heat beans", "heat tortilla", "place beans in tortilla", "sprinkle cheese on top", "roll up"]
```

The methods used in the above code allow us to grab the values of instance variables we set up in our initialize methods. That's why they're called `getter` methods.

For the `Cookbook` class, the title getter method would look like this:

```ruby
class Cookbook
  def initialize(title)
    @title = title
  end

  def title
    @title
  end
end
```

Create the getter methods for the Recipe class that would make our test code work. Validate the functionality of your code in IRB and fix any errors.

<aside>
Why did we use `p` instead of `puts` on lines 6 and 7 of the test code at the beginning of this exericise?

Check it out in IRB. Open up your terminal and IRB and run the following lines of code one at a time:

```console
a = [1,2,3]
puts a
p a
```

Notice how the `p` method prints out the array whereas `puts` creates a new line for each element. This allows us to see what an output is without the formatting that a `puts` statement would add.
</aside>

----

## Setter Methods

Now we want to create `setter` methods so that the the following test code works. The last two lines are new.


```ruby
mex_cuisine = Cookbook.new("Mexican Cooking")
burrito = Recipe.new("Bean Burrito", ["tortilla", "bean"], ["heat beans", "place beans in tortilla", "roll up"])

puts mex_cuisine.title # Mexican Cooking
puts burrito.title # Bean Burrito
p burrito.ingredients # ["tortilla", "bean", "cheese"]
p burrito.steps # ["heat beans", "heat tortilla", "place beans in tortilla", "sprinkle cheese on top", "roll up"]

mex_cuisine.title = "Mexican Recipes"
puts mex_cuisine.title # Mexican Recipes
```

Note how `mex_cuisine.title = "Mexican Recipes"` changed the output of `cuisine_cuisine.title` to be "Mexican Recipes" instead of "Mexican Cooking".

How would you write a method to enable that functionality? That method is called a `setter` method because it sets or changes the value of something.

The syntax for it looks like this:

```ruby
  def title=(new_title)
    @title = new_title
  end
```

Add that method to your `Cookbook` class. Run our test code in IRB and make sure it works.

<aside>
  Note: In the setter method above, the **=** needs to be part of the method name (i.e. no space between title and =). Thus you write `def title=(new_title)` and not `def title = (new_title)`.

  On the other hand, when you use the method, ruby allows a space like so: `mex_cuisine.title = "Mexican Recipes"`
</aside>


Now add setter methods to enable the functionality of the following code when it's added to our test code:

```ruby
burrito.title = "Veggie Burrito"
burrito.ingredients = ["tortilla", "tomatoes"]
burrito.steps = ["heat tomatoes", "place tomatoes in tortilla", "roll up"]

p burrito.title # "Veggie Burrito"
p burrito.ingredients # ["tortilla", "tomatoes"]
p burrito.steps # ["heat tomatoes", "place tomatoes in tortilla", "roll up"]
```

Check your code in IRB.

----

## attr_reader, attr_writer and attr_accessor

Did you notice that writing all those getter and setter methods got tedious pretty quickly?

Instead of writing out each getter and setter method (which would get long quickly), we can use `attr_reader`, `attr_writer`, and `attr_accessor` to accomplish this for us. Using `attr_reader` is equivalent to writing a getter method. Likewise, using `attr_writer` is the equivalent of writing out setter methods and `attr_accessor` combines all of them.

You can add `attr_reader`, `attr_writer`, and `attr_accessor` to your class like so:

```ruby
class Recipe
  attr_reader :title
  attr_writer :steps
  attr_accessor :ingredients

  def initialize(title, steps, ingredients)
    @title = title
    @steps = steps
    @ingredients = ingredients
  end

end
```

`attr_reader :title`, `attr_writer :steps`, and `attr_accessor :ingredients` in the code above are equivalent to these lines of code:

```ruby
# attr_reader :title replaces this getter method
def title
  @title
end

# attr_writer :steps replaces this setter method
def steps=(value)
  @steps = value
end

# attr_accessor :ingredients replaces both getter and setter methods below
def ingredients
  @ingredients
end

def ingredients=(value)
  @ingredients = value
end
```

Replace all your getter and setter methods with the shorter versions we just learned.

Run your test code to make sure it still works.

----

## Getting everyone talking

So now we've set instance variables for when we use our class to make a new object, and we've set up getter and setter accessors that allow us to modify and view these instance variables. How do we go about actually making these objects (instances if our classes) talk to each other?

By using methods! Not only can a method take in strings and arrays as arguments, it can also take objects themselves as arguments.


Let's try using an object as an argument. We've added 3 lines of code to the bottom of our test code:


```ruby
mex_cuisine = Cookbook.new("Mexican Cooking")
burrito = Recipe.new("Bean Burrito", ["tortilla", "bean"], ["heat beans", "place beans in tortilla", "roll up"])

puts mex_cuisine.title # Mexican Cooking
puts burrito.title # Bean Burrito
p burrito.ingredients # ["tortilla", "bean", "cheese"]
p burrito.steps # ["heat beans", "heat tortilla", "place beans in tortilla", "sprinkle cheese on top", "roll up"]

mex_cuisine.title = "Mexican Recipes"
puts mex_cuisine.title # Mexican Recipes

burrito.title = "Veggie Burrito"
burrito.ingredients = ["tortilla", "tomatoes"]
burrito.steps = ["heat tomatoes", "place tomatoes in tortilla", "roll up"]

p burrito.title # "Veggie Burrito"
p burrito.ingredients # ["tortilla", "tomatoes"]


mex_cuisine.recipes # []
mex_cuisine.add_recipe(burrito)
p mex_cuisine.recipes # [#<Recipe:0x007fbc3b92e560 @title="Veggie Burrito", @ingredients=["tortilla", "tomatoes"], @steps=["heat tomatoes", "place tomatoes in tortilla", "roll up"]>]
```

There are two new methods - `recipes` and `add_recipes`. It looks like `add_recipes` is adding the burrito object to an array that represents the collection of recipes in the mex_cuisine object.

Let's create those methods. It makes sense to initialize `Cookbook` with a recipes array since each cookbook should start with not only a title attribute but also a collection of recipes. The collection starts out empty, thus the array initially will be set to empty.

We can then create a getter method for that array.

Initialize `Cookbook` with an empty recipe array:

```ruby
# in Cookbook class
def initialize(title)
  @title = title
  @recipes = []
end
```

Create the getter method for the `@recipes` array or use the `attr` shortcut.

After you're done, go ahead and write a method called `add_recipe` in your Cookbook class.It should allow us to pass in a recipe object (an instance of the class `Recipe`) which can be added to the recipes instance variable in the cookbook using either `<<` or `push`.

Run the test code in the terminal to make sure it's working correctly.

----
## Using separate files to organize your code

At this point you've probably gotten fed up with copying and pasting your test code over and over again.

Now you're ready to appreciate a handy way to avoid that.

In the same directory where you have your `cookbook.rb` file, create another file called `testcode.rb`. Inside `testcode.rb`, copy and paste in the test code we created.

Next, at the very top of `testcode.rb`, write `require_relative 'cookbook'`.

Alright! Now all you have to do is run `load "testcode.rb"` and it will run booth your classes and methods in `cookbook.rb` as well as `testcode.rb`.

What the `require_relative 'cookbook'` command does is grab the code from `cookbook.rb` and input it in the file so that `testcode.rb` looks like this when you load it in IRB:

```ruby
## All the code from cookbook.rb - brought in from using the command `require_relative 'cookbook'`.

class Cookbook
 # all your Cookbook class code
end

class Recipe
 # all your Recipe class code
end



## All the code from testcode.rb - your testcode

mex_cuisine = Cookbook.new("Mexican Cooking")
burrito = Recipe.new("Bean Burrito", ["tortilla", "bean"], ["heat beans", "place beans in tortilla", "roll up"])

# ... etc, etc

```

----

# Using another class's methods

An object will still retain all its methods after being passed in as an argument. This means that the `burrito` object will still have all the setter and getter methods it was created with.

Let's ammend your `add_recipe` method. We still want it to push a recipe into the `@recipes` array but we also want to have a puts statement that tells us what recipe we added.

The output would look like the comment that follows:

```ruby
mex_cuisine.recipes # []
mex_cuisine.add_recipe(burrito) # Added a recipe to the collection: Veggie Burrito
p mex_cuisine.recipes # [#<Recipe:0x007fbc3b92e560 @title="Veggie Burrito", @ingredients=["tortilla", "tomatoes"], @steps=["heat tomatoes", "place tomatoes in tortilla", "roll up"]>]
```

We're still pushing the burrito object into the `@recipes` array after calling `add_recipes` but we want it to additionally output the statement `Added a recipe to the collection: Veggie Burrito`. Notice this statement grabs the title of the object we pass in.

How would you can grab the burrito's title attribute for the puts statement?

But using the burrito object's title getter method in the puts statement:

```ruby
def add_recipe(recipe)
  @recipes.push(recipe)
  puts "Added a recipe to the collection: #{recipe.title}"
end
```

----
## Checking out your Cookbook's recipes

Add the following code to your `testcode.rb` file. The comments next to the code represent the output we want to see:

```ruby

mex_cuisine.recipe_titles # Veggie Burrito
mex_cuisine.recipe_ingredients # These are the ingredients for Veggie Burrito: ["tortilla", "bean"]

```

Implement the methods so that the added code works.

**Hint**: You have an `@recipes` array that has all the recipe objects in our cookbook object. Also, `@recipes` array which means it has elements to iterate through to grab their values.

----

## Exercise #1

Write a `print_recipe` method for the Recipe class that prints a recipe's info - it's title, ingredients and steps. Give it appropriate formatting. You might consider the `join` method for connecting elements in arrays.

----

## Exercise #2 - Add another recipe

In your `testcode.rb` file, first create another recipe and add it to your mex_cuisine cookbook. Your `@recipe` array will now have two recipe objects. Load your `testcode.rb` file to make sure the your code in `cookbook.rb` still works. Fix any bugs.

----

## Exercise #3 - Practice with object methods

Write a `print_cookbook` method for the Cookbook class. It will print the recipe for each recipe in the cookbook - it will give each recipe's title, ingredients, and steps with appropriate formatting.

----

## Exercise #4 - Additional formatting

In the above two methods, `print_cookbook` and `print_recipe`, you printed out the steps for recipes. How would you print them out with step numbers such that the steps for our `burrito` object would look like this:

```text
1. heat tomatoes
2. place tomatoes in tortilla
3. roll up
```

You can either create code to do this or look up a ruby method that could help accomplish it.

----

## Exercise #5 - Create your own methods

Think of at least two more features you'd like to see in this Cookbook application that aren't included and implement them now.

----
## Extension (optional extra practice and challenge)

### Racing cars

You'll be creating a racetrack for cars! You'll be creating an object-oriented system centered around the RaceTrack class and the RaceCar class. This race works a bit differently than normal races. This race lasts 5 hours. Whoever has driven the furthest in 5 hours wins

* A user can add `RaceCars` to `RaceTracks` - similar to how you added Recipes to Cookbook in today's lesson.
* A user can start a race on the `RaceTrack`
* Once a race has started, users can't add more cars
* When the race starts, each `RaceCar` on the track gets a random speed between 60-80 MPH
* A user can forward the race by 1 hour at a time and check how far each car has gotten.
* After every hour of the race, each car's speed increases by a random amount between 0-20 MPH
* At the end of the 5 hours, you can print the winner of the race. You should also set the speed of the cars to 0 to indicate you're resetting the race.


