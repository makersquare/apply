# Coding Challenge

After you've completed the exercises in this course, you can attack this coding challenge. This challenge is to see how well you're able to apply what you've learned about Ruby so far. During your technical interview, we'll go through your code with you and help you make more progress on it.

Put your work on <a href="https://gist.github.com/">gist</a> before the interview. We will pair with you on incomplete portions if needed.

This challenge will test your knowledge of

* Classes
* Methods
* Conditionals
* Loops
* Hashes
* Arrays

**Read through all instructions before getting started!**

----

Create a file called banking.rb

You'll be creating 2 classes in this file. The two classes interact with each other. You'll make the `Person` class and the `Bank` class.

## Person class

A new person should have a name set and should have a certain amount of cash that the person keeps with him/her.

----

## Bank class

With the bank, you should be able to:

* open a new account using the person's name
* withdraw money from a person's account
* deposit money into a person's account
* transfer money to another bank

----

## Extra Credit

This extra credit is meant to be more difficult than the coding challenge alone. As much as you'll be tempted to, do not delay scheduling your interview because of any of the extra credit problems. You should only work on this if you have time before your interview.

**Extra Credit (level 1):** Don't let a person have negative cash. Prevent them from over-withdrawing money.

**Extra Credit (level 2):** Calculate how much money the bank has stored

**Extra Credit (level 5):** Create a credit card system for the Bank. I will leave the interface open-ended. This is to test to see your ability to design a system and implement it.

----

## Examples

Here's an example of how one might use the two classes:

### Creating accounts
```ruby
chase = Bank.new("JP Morgan Chase")
wells_fargo = Bank.new("Wells Fargo")
me = Person.new("Shehzan", 500)
friend1 = Person.new("John", 1000)
chase.open_account(me)
chase.open_account(friend1)
wells_fargo.open_account(me)
wells_fargo.open_account(friend1)
```

Here is what the output would look like:

```text
JP Morgan Chase bank was just created.
Wells Fargo bank was just created.
Hi, Shehzan. You have $500!
Hi, John. You have $1000!
Shehzan, thanks for opening an account at JP Morgan Chase!
John, thanks for opening an account at JP Morgan Chase!
Shehzan, thanks for opening an account at Wells Fargo!
John, thanks for opening an account at Wells Fargo!
```

### Withdrawing and Depositing

Code

```ruby
chase.deposit(me, 200)
chase.deposit(friend1, 300)
chase.withdraw(me, 50)
```

Output

```text
Shehzan deposited $200 to JP Morgan Chase. Shehzan has $300. Shehzan's acccount has $200.
John deposited $300 to JP Morgan Chase. John has $700. John's account has $300.
Shehzan withdrew $50 from JP Morgan Chase. Shehzan has $350. Shehzan's account has $150.
```

### Transfers

Code

```ruby
chase.transfer(me, wells_fargo, 100)
```

Output

```text
Shehzan transfered $100 from the JP Morgan Chase account to the Wells Fargo account. The JP Morgan Chase account has $50 and the Wells Fargo account has $100.
```

### Extra Credit level 1: Validate

Code

```ruby
chase.deposit(me, 5000)
chase.withdraw(me, 5000)
```

Output

```text
Shehzan does not have enough cash to deposit $5000.
Shehzan does not have enough money in the account to withdraw $5000.
```

### Extra Credit level 2: Count totals

Code

```ruby
puts chase.total_cash_in_bank
puts wells_fargo.total_cash_in_bank
```

Output

```text
JP Morgan has $350 in the bank.
Wells Fargo has $100 in the bank.
```

### Extra Credit level 5: Credit Cards

For this open-ended problem, you should create your own test cases and add it to the bottom of your solution

----

Once you're finished, make sure you test your code against the use case and get the same results. Here is what your file should look like:

```ruby
class Bank
  # Your code goes here
end

class Person
  # Your code goes here
end

# Test code:
chase = Bank.new("JP Morgan Chase")
wells_fargo = Bank.new("Wells Fargo")
me = Person.new("Shehzan", 500)
friend1 = Person.new("John", 1000)
chase.open_account(me)
chase.open_account(friend1)
wells_fargo.open_account(me)
wells_fargo.open_account(friend1)
chase.deposit(me, 200)
chase.deposit(friend1, 300)
chase.withdraw(me, 50)
chase.transfer(me, wells_fargo, 100)
# chase.deposit(me, 5000)
# chase.withdraw(me, 5000)
# puts chase.total_cash_in_bank
# puts wells_fargo.total_cash_in_bank
```
