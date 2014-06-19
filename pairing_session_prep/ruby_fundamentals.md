# Ruby Fundamentals

This lesson will introduce how to use IRB (Interactive Ruby Shell), using Ruby concepts that should be familiar to you (variables, hashes, arrays, loops). **Much of this will be a review of previous materials.** Feel free to go at your own pace - you don't have to tediously go through every step, but make sure you understand these concepts.

<aside>
  Remember that if you already feel comfortable with this material, you can skim through it and move onto the next chapter.
</aside>

If your computer doesn't have IRB installed, use this link to do so: [ruby-lang.org](https://www.ruby-lang.org/en/downloads/). Mac users will usually have a version of IRB pre-installed aready. You can check to see if IRB is installed by typing `irb` into the console.

 After you have installed IRB, you can fire up an IRB session from the console like so:

```console
$ irb
```

----

IRB is a way to write Ruby code that is evaluated immediately. IRB stands for "Interactive Ruby Shell" - it's what's known as a **REPL**: a "read, evaluate, print" loop. It allows us to enter Ruby expressions, have them "evaluated" (or run), and the result printed out to the screen, in an endless loop.

Let's open up IRB and try out the following:

```ruby
1 + 2
"usa".upcase
[1, 2, 3, 4, 5].collect { |n| n**2 }
{:first_name => "Harsh" , :last_name => "Patel",
  :employer => "MakerSquare"}.each do |key, value|
  puts "#{key}: #{value}"
end
```

Pretty cool right? Works a lot like [TryRuby.org](http://tryruby.org) — simply type a command in and see instantaneous feedback.

In the exercises below, when you see a a code sample, type (not paste) it into your IRB prompt to try it out for yourself. Feel free to play around with the code samples. This lesson is about review and discovery, and IRB is a great tool for both.

**Protip:** You can hit the up key while in the console to go to the last line of code you entered. Continuing to press the up key cycles through your code by order of most recently entered.
