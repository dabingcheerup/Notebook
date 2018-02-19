In the previous lesson, we introduced some basic concepts, the internet and the World Wide Web, and I mentioned the Uniform Resource Locator, or URL. Which is the Unique address for some piece of content, some data, some resource on the World Wide Web. I also mentioned that there is something known as the protocol,
which is the structure of the content or communication between devices, and we'll start to look into that a little bit more in this lesson.
In the previous lesson, I showed a diagram of the internet, this completely connected graph of devices. Here's a diagram, I suppose, of the World Wide Web. Now remember, _the World Wide Web is this application, the software running on the hardware that is the Internet, but it is also a graph._
The different pieces of content have links to each other that we can think of as edges in a graph. In this particular diagram, Wikipedia is here at the center of the graph of the picture, and we can see there are links to to other pages and
those have links to other pages or other websites as well.

1. How do we view content on the World Wide Web?
    
    Well, in the old days, there were web browsers that were just text. let's say that 1980s, 1990s, we browsed the web using text browsers. We could see the content, we could request content,we could link from one to the other.It looks like this, it was just text.Then somewhere in the early mid 1990s came one of the most popular graphical web browsers known as NCSA Mosaic.Mosaic allowed you to not only go from one piece of web content, one page to another and see the content, but you could also for instance see images so that we could look at pictures of sleeping dogs.

    Nowadays there are five popular web browsers.Chrome, Safari,Opera, internet explorer and firefox. So what do I mean by web browser, what exactly is that._Web browser is a piece of software that is used to access and display content_. That it finds on the world wide web, and let you navigate from one location, one document to another.

    The browser contains three main components, and these are the three, I suppose, cornerstones of web content, and the three things we're going to look at in this course.
    
    1. The first main component of the web browser is known as the **rendering engine**. The rendering engine is what decides what to display and how to display it within the web browser. Thus, things like the presentation, the ordering of things, the content itself, and that uses technologies **HTML and CSS**, which we're going to see later in this week of the course.
    
    2. The other part of the browser is known as the **JavaScript Engine**, that the dynamic part. That's the part that is running code in your browser on your computer, or on your device. That's creating dynamic content, modifying content and that uses JavaScript, which we'll see in the second part of this course.

1. How does a web browser work.

    The most important thing to understand for us as the web programmers or web developers is the **protocol HTTP** or **Hypertext Transfer Protocol**.
    
    1. HTTP is how the web browser communicates with other devices, other computers, on the World Wide Web To request and transfer documents.

    2. HTTP is a client server protocol. There's some computer, which is known as the **client**. Here, we have a little diagram of a laptop. It could be your mobile device. It could be your refrigerator. But, **something that's on the world wide web**. And, there's some server. The **server** is generally some big computer that's Somewhere else, on the Internet, and they're connected of course by the Internet through various connections and devices a long the way. 
    
    In HTTP the client initiates the conversation or the transfer of the data by sending what's known as an **HTTP request**, the **server is out there listening for incoming request** and the client sends the request saying Server, can you please give me some data? The server then decides what to do with that request and sends back what's known as the HTTP response. 
    The **HTTP response** includes the content that the client requested, and then the client figures out what to do with that content. _HTTP is a plain-text, human-readable protocol that's used for exchanging data on the web._ 
    What that means is that if you could open up your web browser and look at the data that's going back and forth, it's just text. You would be able to read it. 
    HTTP is based on the client-server model. The client sends a request, which is not only the content that its asking for, but also information about the client. The server sends back the requested resource or content or page or data, but also information about the server itself.If we could look at all of that content that's going back and forth between the server, and the client, the request, and the response we'd see something that looks like this.

![](/assets/Screen Shot 2018-02-18 at 11.07.56 PM.png)

1. the top is the request. The request is the client or the browser asking the server, can you please give me this information or this resource or this data.
2. All of this down here is the response. Here is the headers of the response. This is information that the server is sending back about the server itself or about the data about the content 
3. And then down here is the content itself, the resource that was requested.

Let's look at more detail about an **HTTP request**.

1. The first line of the request is always a **verb**. The verb tells the server what is the action that the client is hoping to perform. It could be GET, which is saying please give me this resource. I want to get this resource. The verb can be head which is I just want the header information not any particular resource or post.
Which is to creat a resource or create new content on the server.
2. Following the verb is the **argument** and the argument for instance in a get request which we'll see in just a second Is what is the name of the resource or content that's being requested. On that first line on the HTTP request after the verb and the argument is always
3. the **protocol** and these days generally the protocol is HTTP/1.1. The client may send other information about itself, other information about the request book, that's the most important part. Is the verb, the argument and the protocol.

Let's look at an example of an HTTP request in more detail.
The first line is always the request line.
That includes the three important parts that I just mentioned. The first thing in that line is the verb. In this case, it's GET asking the server, please give me this resource. I would like to get this resource. The second thing is the argument or the identifier. Here is some type of URI, some type of identifier that's the name of the resource or the page on the server. And then last on this first line is the the HTTP version.

Following that is some request headers.
It could be things like where is this client? What is the type of web browser it's using, etc? 

There's always a blank line after the headers, and then any other data that the client wants to send to the serve as part of the request. follows after that blank line. 

So the server has received that HTTP request.
It knows the protocol. It knows that they are talking HTTP one dot one, in this case, so it knows what is being requested. And now it can handle that request and send back some sort of **HTTP response**.

1. The first line of an HTTP response always includes the **protocol** and the **status code**. And there are different categories of status codes which could be
just some information.

They're successfully giving you back the content, or
successfully servicing the request. It could redirect There can be types of errors the three most common error
codes is _200 ok which indicates that the request was successful_ and I'm about to give you back the content that you've requested. The one you're probably,
everybody's familiar with is _404 which means not found_. That means that the server could not find the content that was requested And then one that we hope to never run into was _500, which is a server error._
Which means there's some problem in the server, in the software, that's trying to handle that request.

2. Following that first line, which is the status code and the protocol, comes the **header information**, which is information about the server or about the response.

3. Then the **blank line** and then the **body of the response** which in the case of a gap request, would be the content of the resource of the page that was requested,

so here's an HTTP response example.
The first line is always the protocol, and then the status here is 200,okay. Meaning that this request was successfully serviced.

Then we get the r_esponse headers which is just information about the server or about the content that's being sent back._ It has the date, it has the type of the server, it tells what is the content type,
how many bytes are in the content, how many bytes are in the response.

There's always a blank line. And then the body of the response, the requested resource, follows.

To summarize, we've looked at a web browser and
how a web browser works using a HTTP.

A HTTP is this plaint text human readable client server protocol in which a client can request some resource. And the server can send back a response with that resource.
