# Case Statements

We also have another type of conditional in Ruby, the **case statement** conditional. Let's take a look:

```ruby
atm_transaction = "withdraw"

case atm_transaction
when "withdraw"
  puts "Starts withdrawal process"
when "deposit"
  puts "Starts desposit process"
when "cancel"
  puts "Cancels transaction"
else
  puts "Sorry, we don't recognize this transaction"
end
```

Unlike the if/else conditional we learned above, with the case statement conditional, you specify a case condition with `case` (in this situation, a variable containing an ATM transaction) and then you "walk" down through the `when` options until you either find a match or run out of options. The `case` statement can also take an optional else condition that outputs if no matches are found. Let's look at one more:

```ruby
score = 91

result = case score
  when 0..60
    "F"
  when 61..70
    "D"
  when 71..80
    "C"
  when 81..90
    "B"
  when 91..100
    "A"
  else "Invalid Score"
end

puts result
```

This time around we set a `score`, then set `result` equal to a case/when statement using `score`. When we call puts we can now see what the letter grade we received was based on that score. We're always awesome so of course we got the A here.

----

## Exercise 5

Now let's try making a case statement. Make a variable called `fav_command` with your favorite terminal command stored inside as a string, then create a case/when statement for some common terminal commands you've learned so far (like `ls` or `cd`) and have it `puts` what that command does in your own words using your `fav_command` variable. Think of why a case statement might be more useful/easier than if/else in this kind of situation.
