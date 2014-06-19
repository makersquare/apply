# Input/Output

# Programs, Input/Output (I/O) and Networking

Because a programming language is compiled down to machine code but also has the power to utilize the computers operating system's higher-level functions, this gives us the ability to utilize **input/output** (frequently called I/O). All I/O means is that you’re taking something in (input) or putting something out (output)--what you’re putting into or taking out of depends entirely on what you need to use I/O on. Most often, this refers to either filesystems or networking data, but could also refer to video projection/capture, audio playback/recording, or anything else you can imagine! For our purposes, we’re interested in I/O as it applies to network data, which means that we're going back to the stuff we learned previously--data and ports!

To receive input data, we claim/"bind" to a port using our programming language, and then listen for incoming data that's being directed to the port we've claimed. But just because we've bound to a port and are listening, this data still isn't much but a plain "stream" of network data without any structure or meaning! We need to give that information meaning. Enter a new protocol called **HTTP**.
