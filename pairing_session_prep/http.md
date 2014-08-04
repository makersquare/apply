# HTTP



# Hypertext Transfer Protocol (HTTP)

Did you notice how in the section on data transfers we only talked about receiving data to ports in one direction? In reality, most internet communication happens in both directions, with data getting passed back and forth between two computers in sequence. Think of it like computers "talking", the same way how in a conversation you say something to someone, they talk back, you say something, they say something, and over, until the conversation is complete. A computer conversation can be as complex or as simple as you want, depending on the set of rules those computers' communicating applications have agreed to use (remember that term "protocol"?). Here's an example of what a data-conversation between two computers could look like:

```
COMP1: ARE YOU THERE?
COMP2: YES
COMP1: COOL. CAN I ACCESS YOUR FILES?
COMP2: YES
COMP1: COOL. PLEASE GIVE IT TO ME
COMP2: HERE YOU GO <FILE>
```

Another one might look like:

```
COMP1: ARE YOU THERE?
COMP2: YES
COMP1: COOL. CAN I ACCESS YOUR FILES?
COMP2: YES, BUT ONLY IF YOU ASK NICELY (ACCESS CODE)
COMP1: I DON’T HAVE AN ACCESS CODE. PRETTY PLEASE GIVE ME YOUR FILES?
COMP2: ACCESS DENIED
COMP1 (thinking): HMM. I KNOW I HAVE ANOTHER COMPUTER THAT CAN GIVE ME WHAT I NEED TO ACCESS THIS ONE
COMP1: COMP3, ARE YOU THERE?
COMP3: YES
COMP1: I NEED ACCESS CODES FOR COMP2
COMP3: ACCESS CODE: 0100100101010101!
COMP1: COMP2, ARE YOU THERE?
< COMP2 has connection problems>
COMP1: COMP2, ARE YOU THERE?
COMP1: COMP2, ARE YOU THERE?
COMP1: COMP2, ARE YOU THERE?
< COMP2 COMES BACK ONLINE >
COMP1: COMP2, ARE YOU THERE?
COMP2: YES
COMP1: PLEASE GIVE ME YOUR FILES. ACCESS CODE: 0100100101010101
COMP2: HERE YOU GO <FILES>
```

The previous example is a little bit silly, but it could describe an inefficient program's behavior (COMP1) to check another computer's (COMP2) application's availability, receive a confirmation, check for permissions to access files, hear back that it needs to "ask nicely", try its best to request the files, and then be told no. COMP1 might then think that it knows of another, remote computer (COMP3) that can give it an access code, and then receives the code from that. COMP2 has issues with its internet connection and COMP1 repeatedly tries to "ping" COMP2. COMP1 might decide after a certain number of tries or a certain time that it's done trying and give up, but in this case COMP2 responds soon enough and returns confirmation. COMP1 requests the files with their shiny access code, and COMP2 coughs them up.

Of course, like we said--a little silly. The web operates on a much simpler and to-the-point protocol called the Hypertext Transfer Protocol (HTTP) and an example exchange looks like this:

```
BROWSER: GET ME http://www.makersquare.com/. BY THE WAY... I'LL TAKE TEXT IN ENGLISH, WHATEVER EXTRA DATA YOU THINK I MIGHT NEED, AND I'M GOOGLE CHROME
WEBSITE: OK. HERE IS http://www.makersquare.com/ AS AN HTML PAGE. BY THE WAY... IT'S 10652 BYTES LONG, TEXT IN ENGLISH, RENDERED TODAY, BUILT WITH RUBY.
```

What you're seeing here is the Request-Response format of HTTP. Originally built with simple linked text pages in mind ("Hypertext"), HTTP protocol says that you must a define a set of headers as well as a "request method" and send them as part of a **request** to a website. Note that there's nothing inherently special about a request--it's merely a set of headers that web applications expect to receive and respond to--hence it being a "request" for a "response". Here's what a minimal HTTP request header looks like:

```
GET / HTTP/1.1
Host: www.makersquare.com
```

This means: use the GET request method towards the root url (/), with version 1.1 of HTTP. Host: specifies the URL, which is www.makersquare.com. In total, this means "Using a GET request method recognized by version 1.1 of HTTP, get me www.makersquare.com/". If our GET line was "GET /team", you would be saying "get me www.makersquare.com/team".

You might be wondering what a "request method" is. It's simply a type of request that the receiver of the request expects. The set of rules defined by HTTP states that these request methods must be used to request certain things specific to their method. There's nothing inherently special about them otherwise: the developers of the protocol just want you to make your applications communicate in a certain way. There are four commonly used request methods: GET, POST, PUT, and DELETE. The two that are most immediately important to you right now are GET and PUT, which you will learn about in the primary course. Just remember that they're simply ways to indicate to the website we're sending the request to that "Hey, I want you to give me something in a certain way." Let's move onto the Response part of HTTP.

Here's an example of the HTTP response that a website gives back to a successful request:

```
HTTP/1.1 200 OK
Date: Mon, 23 May 2005 22:38:34 GMT
Server: Apache/1.3.3.7 (Unix) (Red-Hat/Linux)
Last-Modified: Wed, 08 Jan 2003 23:11:55 GMT
ETag: "3f80f-1b6-3e1cb03b"
Content-Type: text/html; charset=UTF-8
Content-Length: 131
Accept-Ranges: bytes
Connection: close

<html>
<head>
 <title>An Example Page</title>
</head>
<body>
 Hello World, this is a very simple HTML document.
</body>
</html>
```

What's happening here? A bunch of stuff. First, we're returning the version of HTTP the site implements, as well as what's called a **status code**. In the same way that a request method indicates a certain type of request, a status code indicates a certain type of response from the website. Here it says 200, OK, which means "everything went as planned". There are status codes starting in 100, 200, 300, 400, and 500, and they all mean different things. Here's a listing of them:

- 1xx - Informational. Request received, continuing process.
- 2xx - Success. We got what you meant.
- 3xx - Redirect. The site moved! I'm changing where you are.
- 4xx - Client error. You did something wrong. You know 404 errors? That means "page not found".
- 5xx - Server error. The website did something wrong. We didn't code our site right, sorry. The most common is a 500 Internal Server error.

You've probably seen some of these already on almost-blank white pages with black text telling you stuff. This is what those are--just status codes from websites. Let's keep reading!

Next we get the date, the type of software hosting the website, the last time the webpage was modified, some cache information (this isn’t really important to you right now so don't worry about it), the type of content you've received and its length, and other information about your connection to the website. After the line break, we get... HTML! Finally, after all this reading, we have *files*!

So what happened here? In a nutshell, we sent a request to a website and it sent us back an HTML file. But wait... we didn't do this ourselves within our programming language. Last we saw, we were still accepting unstructured data to our port. That's correct--instead, we’re using a web browser, which is a piece of software designed to send and receive HTTP requests and responses and decode the data received into a viewable site. Most of the users of the web utilize web browsers that automatically make HTTP requests on behalf of the user whenever the user navigates to a URL. The website sends a response back to the browser at port 80, and the browser takes that data, structures it in a readable format, does a bunch of housekeep-y, program-y stuff, and then renders it to the screen so that you can browse your favorite websites. This all happens underneath the hood and most people have no idea how it works--and they don't need to. But to make web applications, *you* absolutely need to know it!

Yet, we still don't know how to make something happen with our programming language. What do we do so that we can set up our own site? Enter the **web framework**.
