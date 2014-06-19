# Math


## Numbers in Ruby

Ruby has a few types of numbers, but the ones we are going to focus on for the minute are **integers** and floating-point numbers (**floats**). You may recall from school that integers are whole numbers and floating-point numbers are numbers that have a decimal.

```ruby
1 # integer
3.14 # float
```

We also have access to all the basic mathematical operations we all know and love:

```ruby
2 + 7  #=> 9
5 - 3  #=> 2
8 * 8  #=> 64
12 / 3 #=> 4
2 ** 3 #=> 8 (2 to the power of 3)
10 % 3 #=> 1 (remainder of 10 divided by 3)
```

Pretty basic stuff, except for maybe the `%` (**modulo**). The modulo works a lot like division, but instead of returning the result, it returns the remainder. So `9 % 3` returns `0` and `11 % 3` returns `2`.

Now what if you have a float that you would prefer to be an integer, or vice-versa? How do you convert between the two? What about converting to other data-types?

```ruby
3.14.to_i     #=> 3
9.999999.to_i #=> 9
2.to_f        #=> 2.0
3.to_s        #=> "3"
```

Note that you lose some information going from floats to integers, since it always rounds **down** to the nearest whole number.

----

## Testing Out Division in IRB

Try dividing integers in IRB and see if anything seems weird to you (e.g. `7/2`). Why do you think this is? Now try dividing floats and see if that matches your expectations more (e.g. `7.0/2`).
