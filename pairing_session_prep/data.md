# How does data get from computer to computer?

How does data travel over the internet? Some will jokingly tell you that it's a series of tubes, but that's actually not too far from the truth--more specifically, it's a wide array of cables that are connected to internet service providers (ISPs) like Comcast, Time Warner Cable, Road Runner, AOL, and more that connect you to the internet.

Your computer sends out data, which gets converted by its hardware into electrical impulses that travels through these cables. Another computer picks up that data, and then translates that with its own hardware, back into data that it can understand. The way this data actually finds the right computer on the internet is complicated enough that it won't be covered here, but it's also interesting enough that we recommend you read about it in <Networking TCP/IP post>.

# How does a computer know what to do with data it receives?

Data sent between computers can be any series of binary numbers (that is, 0s and 1s). This data is always packaged with something called a **header**, which is a certain amount of binary information that tells the computer that receives it what the data is for. It contains information like the length of the data, what computer it came from, what the data is supposed to be used for, and more. This information is called a "header" because it's prefixed to the beginning (a-HEAD) of all the data getting sent.

When a computer receives that data, it takes out all the header information, which it then reads. Because that header tells the computer about the data it’s attached to, the computer knows how to decode those 0s and 1s into a certain format that a specific application on the computer can use. For instance, when you use your web browser to visit a website, the header attached to the data from the website tells *your* computer that the data is meant to go to your web browser. Your computer says "OK!" and then translates that data into something that your browser can display.

What in the header of a piece of data tells your computer what application to use? That's called the **port**.

----

# Ports in a storm (of data)

If we didn't have (sea) ports, ships would have nowhere to come home to out of a storm. In the same way, (computer) ports help data find their way to the right application on a computer. Each application on a computer that needs to be connected to the web has its own port. A port is represented by a number from 1 to 65535. About 250 ports are reserved for common usage, but otherwise you can assign your applications to use any port. Some applications even use multiple ports! (For instance, the game World of WarCraft uses the ports 3724, 1119, 1120, 4000, 6112, 6113, 6114, 80, and 6881-6999.) The most common port you may have already heard about is port 80, the port used by all websites. Don't believe me? Try this:

1. Open up your favorite web browser
2. Navigate to www.facebook.com:80 (or any website you like with a :80 on the end)
3. Watch what happens.

The :80 disappeared! Why is that? Because browsers already *know* you're going to get data pointed to port 80, so they take the port number off automatically. This is to avoid confusing users who don't know what a port is. If you visited a website that happened to be hosted at another port, the port number (perhaps :1234, :5231, or something else) would stay there. As a matter of fact, when you develop and host your own web applications, you'll make them use a port that is not :80 (most often :3000) and have to visit them directly at a url like 0.0.0.0:3000.

To further the seafaring analogy, you can think of each computer as being an island with a bunch of different ocean ports (actually computer networking ports) that ships (network data) can land in. The fronts of those ships have signs on them (header information on data). The island then magically directs the ships to the right port. If there is no port available, the ships crash on the shore and then wash away into the ocean, having no effect (the computer doesn't do anything with the data).

(Technical aside: What's a port, really? It's just an identifying number that any application can claim, also known as "binding to a port". The computer itself does most of the work with something called the "transmission control protocol layer", which you can think of as a low-level (close-to-the-hardware) program that follows a set of rules. This set of rules is referred to as a "protocol", and the transmission control protocol layer is more commonly called "TCP". By obeying its rules, TCP layer directs data to different applications that are currently running based on the port they've claimed. So if the TCP layer sees data coming in pointed to port 80, it asks, "Is there a program that's claimed port 80 around?" and then a program either says "Yes! I'm here!" or no program responds at all. If the first one happens, the data is directed to the program that claimed that port. If the second one happens, the data is simply discarded.)

So, what's next? Next we'll be learning a little bit about how programming languages interact with your computer and the web, web frameworks, and things you're used to seeing: websites and their files. Feel free to take a breather and stare out a window for a bit before you move on; you're learning a lot!
