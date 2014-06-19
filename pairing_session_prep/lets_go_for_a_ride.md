## Let's Go for a Ride

I want to create a class that can simulate a car. I'll list out the specs first and then give step by step instructions on how to attack the problem.

* I want the car to keep track of it's position and how much gas it has
* When I call the method **setup** on the car, it should set the position to 0 and gas to 10 (gallons)
* I should be able to drive the car and tell it how many miles to drive. The car should adjust it's position and gas mileage here
* I want the car to be able to fill up gas and print out how much the gas cost

----

## Let's Create a Ruby Project

* Within terminal, type `touch car.rb`
* Type `subl .` to open up your text editor
* Open the file `car.rb`

In `car.rb`, create a new class called `Car`. For now, we'll have no content in it.

Load the class in IRB and create an instance of the car class.

Great! The printed message is weird and cryptic, so let's change that up.

Create a method called `get_info` that sends back the message "I'm a car!". You can explicitly send back a message by typing `return "I'm a car!"`. Try that out.

* Load the file in IRB again.
* Create an instance of a car
* Take the instance and run the `get_info` method on it

Ruby is full of shortcuts though. A Ruby method will automatically send back the result of the last line of code in the method. If you get rid of the keyword **return**, you'll get the same result.

The code you wrote should print out "I'm a car!" to the console now.

Now let's create a method called **setup**. This method should set 2 instance variables.

* It should set `@fuel` to 10
* It should set `@distance` to 0

We can also edit the `get_info` method to give some info about the fuel and distance. Example:

"I'm a car. I've driven 20 miles and have 5 gallons of gas left."

To make sure `@fuel` and `@distance` have values, run the `setup` method immediately after creating the object, but before printing it.

<aside>check out the error you get if you try to print the object without calling setup</aside>

----

I don't know about you, but I have a major problem with this **setup** (Excuse the pun). But really, if someone wants to use our class, they would have to know that they can't use the method to_s without running setup first. Keeping arbitrary rules for your classes is a bad practice!

## Initialize

Lucky for us, there is a special Ruby method, that if defined, will run every single time you create a new instance. This method is called **initialize**

When you call `Car.new`, the object that it returns will run the method `initialize` automatically, so you don't have to call it manually. In our case, we can just rename the method setup as initialize and delete the call to setup.

Inside your newly named method **initialize** include a puts statement (`puts "the initialize method is running automatically"`).

Try it out by running the Ruby code in IRB.

Let's take the car for a spin! Create the `drive` method which should take an input for the number of miles driven. Change the position accordingly and reduce the fuel at a rate of 20.0 miles per gallon.

To test this out:

1. Load the file in IRB
2. create 2 cars: `car_a`, `car_b`.
3. Print each car
4. Drive `car_a` 10 miles
5. Print the status of both cars. Make sure `car_b` hasn't changed and that `car_a` has the proper changes
6. Drive both cars a distance of your choice and make sure they update accordingly

What happens when you try to drive 500 miles? Prevent that from happening. Make it so that you can drive up until you reach 0 gallons and then print out a message saying you're out of gas and need to fuel up.

Create a `fuel-up` method, which figures out how much gas you need to fill into order to reach a full tank at 10 gallons. Fill it up and print a message telling you how much it'll cost. The cost of gas is $3.50/gallon.

Test this out too.

In terminal `git add` the new file and commit it

Sweet! We have our first functional class! Give yourself a pat on the back and take a break for 5 minutes.
