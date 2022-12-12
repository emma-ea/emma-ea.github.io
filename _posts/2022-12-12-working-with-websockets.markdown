---
layout: post
title: "Working with Websockets"
date: 2022-12-12 19:27:00 +0000
categories: android, flutter
---

I recently got to work on a Flutter project, and I had to use websockets. Being the first time using the protocol, I initially
a couple of mistakes, like using the HTTP protocol scheme as part of the URL scheme. I know you're laughing at me now,
but it was my first time implementing websockets in an app.

With the idea that most things work similarly, I went ahead without looking much into documentation or articles as to how
websockets work. After some Googling, I learned enough about websockets to get my application running, and I think websockets is
a cool protocol that you should use if you have a suitable use case.

### Define Websockets

Websockets is a communication protocol that is considered an upgrade over HTTP. The main catch with web sockets is that, unlike
traditional HTTP connections, where after a client receives a response from a request it makes to a server, the server closes
the connection. There are other techniques for persisting or keeping the connection alive, but as I studied more
into Websockets and HTTP protocols, I got to know this "keep-alive" setting for HTTP protocols may have its downsides.

Going back to web sockets, I hope to cover more on that.The entire idea behind websockets is that once a connection is created 
with the server, There is a bi-directional, full-duplex communication link established. This comes with the perk of being 
low-latent. `Low latency in computer networks mean there is minimal delay in processing volumes of data messages.` Hence its suitable 
for online multiplayer games, chat applications, sports or financial applications where change in data should be readily available 
to users/clients.

### Style

Unlike HTTP, websockets also have their own url scheme, which helps identify websocket connections.
An example in Dart/Flutter:

{% highlight dart %}
// parse uri
val uri = Uri.parse("ws://some-realtime-app");
val channel = IOWebSocketChannel.connect(uri);

// send message
channel.sink.add("some-message-to-server");

// listen to server
channel.stream.listen((event){ /* handle some response stream */ });
{% endhighlight dart %}

This connection establishment happens over a single TCP connection, and attaching event handlers allows you to know the state of
of the connection. In Dart/Flutter, the web_socket_channel package provides a cross-platform wrapper to use websocket connections.
on Android and iOS devices. Take a look at the package on Flutter pub.dev if you want to play around with it.

### WebSockets Usecases

Because most applications require real-time data to be consumed by their clients, it is critical that you understand the use case of 
the application or project and select the appropriate technology. I've attempted to list a couple of use cases that require 
websockets implementation below: 

* Financial tickers
* Multiplayer games
* Sports updates
* Social Feeds / Messaging / Chat applications
* Location-based apps

### My take

Initially not being familiar with websockets, I intended on building the project that introduced me to websockets by using a
technique called Periodic Polling,  where after a certain duration, the client device makes a request to the server for new data,
If any, the fetch data is updated. Actually, this was my initial idea for solving the issue of getting real-time data.

This not only has some downsides like HTTP overhead, constant querying for new data. But it would also take additional time.
implementing this periodic scheduling for data. I'm fairly new to this, and after reading in a few places, I discovered
there are other methods, like `Long Polling` by which the connection to the server is kept alive and the server returns
a "new" response after a certain period.

Looking at websockets, once the connection is established and messages are sent to the server. There will be no need to constantly 
query the server for new data, unless a different message is sent for new data. You just have to setup a listener, and once new 
data becomes available, it is sent to its consumers.

To end here, I think Websockets are a cool protocol. I hope to use it more and experiment with it. see you in the next one.


