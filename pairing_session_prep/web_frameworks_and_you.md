# Web Frameworks and You

As we've discussed, a programming language built on top of a robust OS has all the tools you need to implement your own networking protocols. But implementing an HTTP-compliant program is [difficult, and irritating](http://www.w3.org/Protocols/rfc2616/rfc2616.html). Ruby's core library actually *has* tools that can help you implement HTTP, but then you would have to take care of all sorts of other website stuff like send back your own files manually, keep track of session variables, write your own integration with some sort of data storage mechanism, and more. All that is very practice-worthy, but we're here to make web applications, gosh darnit. Reimplementing all that would be like reinventing the wheel, because a web framework for just about every major programming language exists. For Ruby, that web framework is Ruby on Rails.

Ruby on Rails essentially sets up what we call a "web server", so named because it *serves files* to users on *the web*. In fact, any relationship between a browser and web server is known as a **client-server relationship**. I don't know the etymology of the term client, but I always think of it in terms of the person ordering/getting something from the service/server--hence, a client of the server. But what does a web server actually do? A lot of things, actually. Things like:

1) Routing requests to any URL you want
2) Serving files and other assets
3) Managing internal memory
4) Keeping track of stored data
5) Helping you keep your code sane and organized
6) a heck of a lot more

Any good web framework comes with the tools that allow you to create a fully-fledged, exciting web experience. After creating a website in Rails, you'll have your very own dynamic website application running on port 80, receiving and sending HTTP requests and responses, delighting users left and right. But hold on a second...

... What does "dynamic" mean?

# Hypertext Markup Language (HTML)

To answer the question of what a "dynamic" website is, we first need to explore what a not-dynamic, or **static** website is. Back in the early days, it wasn't really possible to "log in" to a site, or comment, or do anything but send an email manually to the email address listed on the website with your favorite email application. These websites were all made with HTML, or Hypertext Markup Language. Notice how the "H" in HTTP and HTML both stand for Hypertext? That's because HTTP was invented back in the day, when HTML was all there was.

So what's a **markup language**? Essentially it's a language used to define meaning and hierarchy of meaning--or, to “mark up” content. It won't be covered too thoroughly in this lesson since the rest of the prework deals with HTML, but in a nutshell you can use it to define a document with certain "tags", or "elements" that have specific meanings. Web browsers then display this document and use different visual formatting depending on the kinds of elements you used. HTML can also include things like images, tables, and basic formatting elements. Of course, the web was pretty dull for a while, so people figured out a way to make it look cool. Enter CSS.

# Cascading Style Sheets (CSS)

Cascading Style Sheets, or CSS, are a **presentation language** that is tightly integrated with HTML. For the same reasons as above we won't be covering it in-depth, but you can use **selectors** to “select” specific HTML elements/tags and their attributes, and create visual changes including layout, color, borders, and more. CSS can either be included in a separate file, or added inside of an HTML file. Either way, the HTML file loads the CSS file. Then, people realized that sites looking cool was awesome, but they couldn't *do* much, so a guy named Brendan Eich (you might have heard about him in recent news) invented a language called JavaScript.

# JavaScript (JS)

JavaScript, or JS, interacts with the internal representation of HTML that the browser creates. It allows developers to make sites where the content changes and data can be changed--but only in the browser, not the server. It's responsible for that horrible/amazing era of web design from the 1990s. Remember when snowflakes would follow your cursor? JavaScript. Nowadays, of course, JavaScript is actually well-respected and has even moved to the server. But before that happened, the guys at Microsoft figured out a way to make the browser send a request to the server without the user having to navigate to a new page. This was an awesome development, and AJAX was born, forever changing the web.

# Asynchronous JavaScript and XML (AJAX)

Ignoring the confusing name, AJAX enables developers to make HTTP requests without having to reload the page or navigate to a new one. Prior to this, any HTTP request had to happen either through navigation, refreshes, or by submitting forms. AJAX let developers implement things like live updates, real-time communication, and other really cool things that made the web plain easier and more fun to use. Of course, we still haven't talked about where that data and interaction COMES from...

# Databases and Templating

On the web framework side of things, we have a place we store data known as a **database** (a base for your data). We can store any type of data in it and access it through our web framework. In it we can store users, blog posts, comments, articles, or any other kind of information that we might want to change or pull up later. The database is the key component to what allows sites to have any sort of interactivity at all. Everything goes into the database, then comes out as information. But how do we get this information onto the page for users/browsers to see? We need to use something called **templating**.

Browsers have to load .HTML pages. There is no other filetype that they'll render that will also include CSS, JavaScript, images, and other inline content automatically. However, HTML is a static filetype. We can only serve it as it is to the browser. *After* we serve it, we can alter it with JavaScript, but that JavaScript stays in the browser and there's no way for us to interact with it. (Actually, there is, but we won't be covering that in this lesson.) In order to load our data into the web framework, we have to *create* HTML pages on the fly and *then* serve them to browsers that make requests to our pages. We do this with something called a **templating language**.

A templating language is essentially HTML with superpowers. You define a filetype (in Ruby it's .html.erb) associated with a templating language and put your HTML inside. The magic happens when you decide where you want your custom data to go. You use a certain syntax to indicate "hey! data goes here", and the web framework will load it in. You can even put code and logic into it. For example, here's a snippet of code from Ruby on Rails' [Layouts and Rendering example page](http://guides.rubyonrails.org/layouts_and_rendering.html):

```
<%% @books.each do |book| %>
 <tr>
   <td><%%= book.title %></td>
   <td><%%= book.content %></td>
 </tr>
<%% end %>
```

This code is looking for a local set of values named "books", then it repeatedly prints out the HTML inside the "<%% @books.each do |book| %>" and "<%% end %>" lines for each value in that set of books, grabbing each book's title and its content. This might seem like it has no context at the moment, but we would do something very specific with this file: we load it into our web framework, and then have the web framework use it as a "template" to put information and values from our database (or whatever we want to go there based on our code) into it. This process of putting our values inside this template is known as **interpolation**.

So a request might happen like this:

1. A client requests a specific page
2. The website, because of its values in its database/framework, happens to know that this user is already logged in
3. The framework fetches the user's name/other data from the database
4. The framework, based on the page requested, loads up a specific *page template*
5. The framework *interpolates* the user's data into the page template, resulting in a temporary file with all the right data
6. The framework sends the temporary file over the internet as a response back to the client with some headers
7. The client sees that page with their name on it!

The same thing can happen with AJAX, except that it could be triggered by any JavaScript-level event that causes the web framework to process information and return it, optionally interpolating any data necessary. This here is the core of how a dynamic website works and serves the user with such an enriched, exciting experience.

----
