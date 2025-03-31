## Threading Extra

### Topics
1. Launch & Debug Setup
2. App Setup
3. TCP Sockets
4. UDP Sockets
5. Image Syncing

**Source Repository**
* Networking https://github.com/andyguestysj/client-network.git

## Launch & Debug Setup

<div style="position:relative;padding-bottom:56%;padding-top:20px;height:0;"><iframe src="https://hml.yorksj.ac.uk/player?autostart=n&videoId=JggHb59h&captions=y&chapterId=0&playerJs=n" frameborder="0" scrolling="no" style="position:absolute;top:0;left:0;width:100%;height:100%;" allowfullscreen></iframe></div>

For the networking example I've created an application that can be run as a server or a client and for TCP, UDP or as a TCP image syncing example. To make this work I needed a way to identify what to do when I run the code.  

### Command Line Arguments

I've done this using command line arguments. To run the app, the command line is as follows

```console
my-app APPTYPE SERVER|CLIENT
```

where APPTYPE is TCP, UDP or STREAMER and you use SERVER or CLIENT depending on which you want to run. The three APPTYPEs will be explained as we go through them.

The `main()` function in the app looks like this

```java
public static void main(String[] args) {

    boolean isServer = false;

    System.out.println(args[0] + " " +args[1]);

    if (args.length > 1 && args[1].equals("SERVER")) {
      isServer = true;
    }
    // Snipped stuff
}
```

The command line arguments are passed to `main()` as an array of strings `String[] args`.

We can access them and check to see what values they have just like any other array of strings.

Two things to note.

* We need to check how big the `args[]` array is before we try to see what values are in it. If no command line arguments were passed and we try to see what `arg[0]` is we will get an error. We can check the size using `args.length` as in the code above.
* Reminder to see if one string is the same as another string we have to use `stringName.equals(aDifferentString)` **not** `stringName == aDifferentString`. The `==` checks to see if they are the *same object* and doesn't return true if they are *different objects* containing the *same string*, and that is what we want to do.

### VSC & running Code using command line arguments

Using command line arguments in VSC isn't very intuitive. There is an easy way to do it but it takes a bit of setting up. I've set it up for you in the demo code.

On VSC's left hand side button bar there is a button that looks like a play button with a bug on it. This button opens and closes the **Run and Debug** panel.

In a new project this panel will have a big blue button labelled "Run and Debug" which will, surprisingly, run your code in debug mode. 

In the demo project for this topic you will see the panel contains sections for Variables, Watch and Call Stack. You can ignore them and instead look at the drop down menu at the top of the panel. If you have a look at the menu you will see the following entries.

```console
STREAMER CLIENT
STREAMER SERVER
TCP CLIENT
TCP SERVER
UDP CLIENT
UDP SERVER
...
```

There are others below that but you can ignore them.

These six rows represent running the code using the two words as the command line argument for the app. To run the TCP server you select the ```TCP Server``` option from the list and then press the green play triangle next to the name when the list closes.

I'll explain how to do this so everything works as I talk about the versions but basically always launch the server for the app type (TCP, UDP, STREAMER) first and then the client. (The server patiently waits for a client but the client assumes the server is there and tries to connect causing it to crash if the server isn't running. Feel free to improve this and let me know how you did it :-).

These Run And Debug options are saved in a file called `launch.json` in the `.vscode` folder of the project. You can use these as a template for different setups. If you are working with a new project without a `launch.json` file you can create it from the Run & Debug panel.

## App Setup

You'll see I've split the code in this project across a number of sub-folders. Each sub-folder is a different *Java package*. This is simply done for tidyness, each use of the application is largely self contained so can live in its own package. Each package follows a similar structure since each use of the application involves a client and a server.

## TCP Sockets

OK on to the networking stuff proper.

We'll start with sending messages between a client and server using TCP sockets. This will be a very simple setup where we:
1. Start a server which will wait for a connection
2. Start a client which connects to the server
3. The client sends a text message to the server
4. The server receives the message and outputs it to the screen
5. Both server and client shut down and exit

### TCP Server

We'll start with the server and we'll use a top down design approach again.

So first off we need a server so we'll create a `TCPServer` class.

That class will need a constructor to set things up and we know to use sockets we need a port number so we'll pass them in to the constructor. We don't need an IP address, the *client* needs to now the *server's* IP address to speak to us, we'll let the client worry about that.

In the constructor we will set up a socket we can use to listen to for incoming connections. Trying to do this might fail spectacularly so we use a try/catch just in case. (I won't keep repeating this, if you see a try/catch its there for that reason!).

We should also close the socket before exiting the app so we'll create a `close()` method to do that.

```java
package com.TCP;

public class TCPClient {

  ServerSocket serverSocket;

  TCPClient(int portNo) {
    try {
      serverSocket = new ServerSocket(portNo);
    } catch (IOException e) {      
      e.printStackTrace();
    }
  }

  public void close(){
    try {
      serverSocket.close();      
    } catch (IOException e) {
      e.printStackTrace();
    }    
  }
}
```

The server needs to wait till a connection is made before doing anything else. `serverSocket.accept();` *blocks*, or sits doing nothing till a connection is received. We store a socket connecting us to the client that has connected to us in `clientSocket`.

So we need to store `clientSocket` and close it on exit too.

```java
package com.TCP;

public class TCPClient {

  ServerSocket serverSocket;
  Socket clientSocket;

  TCPClient(int portNo) {
    try {
      serverSocket = new ServerSocket(portNo);
    } catch (IOException e) {      
      e.printStackTrace();
    }
  }

  public void close(){
    try {
      serverSocket.close();    
      clientSocket.close();  
    } catch (IOException e) {
      e.printStackTrace();
    }    
  }

  public void awaitConnection(){
    try {
      clientSocket = serverSocket.accept();
    } catch (IOException e) {      
      e.printStackTrace();
    }
  }
}
```

The only thing left to do is handle a message when we receive it.

Here we set up an input stream, read the data (as bytes), convert it to a string and return it.

```java
public String getMessage(){
  String message="";
  try {
    System.out.println("waiting msg");
    InputStream in = clientSocket.getInputStream();
    byte[] content = in.readAllBytes();
    message = new String(content);
                  
    System.out.println();
    //OutputStream out = clientSocket.getOutputStream();
    in.close();
  } catch (IOException e) {      
    e.printStackTrace();
  }  
  return message;
}
```

That's it for our TCP Server. We'll handle using it in TCPSetup but first we'll look at creating our TCP client.

### TCP Client

Again we'll create a TCPClient class and its constructor. This time we need to know the IP address of the server as well as the port number to talk on. 

We also create a `close()` to tidy up.

```java
package com.TCP;

public class TCPClient {

  Socket toServer;

  TCPClient(String serverSocket, int portNo) {
    try {
      toServer = new Socket(serverSocket, portNo);
    } catch (IOException e) {
      e.printStackTrace();
    }
  }

  public void close() {
    try {
      toServer.close();
    } catch (IOException e) {
      e.printStackTrace();
    }
  }
}
```

Other than that all we need is a method to send a message.

```java
public void sendMessage(String message) {
  System.out.println("sending msg");
  try (OutputStream out = toServer.getOutputStream()) {
    out.write(message.getBytes());
    out.flush();
    out.close();
  } catch (IOException e) {

    e.printStackTrace();
  }
}
```

That's it.

### TCP Setup

The TCPSetup class is there to handle running both the server and the client.

This should be fairly obvious what it does.

The only thing to note here is that the client setup gets the IP address of the machine its running on and uses it for the server address. This works fine for running and testing both client and server on a single machine. To connect to a server running on a different machine change the lines

```java
InetAddress host = InetAddress.getLocalHost();
TCPClient client = new TCPClient(host.getHostName(), portNo);
```

to 
```java
InetAddress host = InetAddress.getLocalHost();
TCPClient client = new TCPClient("XXX.XXX.XXX.XXX", portNo);
```

where "XXX.XXX.XXX.XXX" is the ip address of the server.


```java
package com.TCP;

import java.net.InetAddress;
import java.net.UnknownHostException;

public class TCPSetup {

  public TCPSetup(boolean isServer, int portNo) {

    if (isServer) {
      System.out.println("TCP Server started");
      TCPServer server = new TCPServer(portNo);
      boolean running = true;
      while (running) {
        server.awaitConnection();
        System.out.println("Server detected lient connected");
        running = false;
        String message = server.getMessage();
        server.close();
        System.out.println("Server received message : " + message);
      }
    } else {
      System.out.println("TCP Client started");
      try {
        InetAddress host = InetAddress.getLocalHost();
        TCPClient client = new TCPClient(host.getHostName(), portNo);
        System.out.println("Client connected");
        String aMessage = "Hello Andy";
        client.sendMessage(aMessage);

        System.out.println("Message sent \"" + aMessage + "\"");

        client.close();
        System.out.println("Client closed");
      } catch (UnknownHostException e) {
        // TODO Auto-generated catch block
        e.printStackTrace();
      }
    }
  }
}
```

## UDP Sockets

The UDP Sockets version is almost identical to the TCP sockets code so I won't go through it. Note that the way the sockets are used is a little different.

## Image Syncing

You should be able to work out how the Streamer code works now (with a little bit of remembering the last two sessions).

Here a server is started that sits waiting for a connection.

A client is started that sits watching the image file "rubbish.png" in the "ClientFile" folder. If the client detects that the file has been changed it loads it in to memory and sends it through a TCP socket to the server. It then goes back to waiting for the file to change.

When the server receives an updated image it saves it to the file "rubbish.png" in the "ServerFile" folder and then goes back to waiting for a connection.

So the app, when both server and client are running, should back up the "rubbish.png" file every time it is changed.

Note we include a pause in the client between it detecting a change in the file and trying to read it. If we read the file too quickly when the file is changed we can't read it and get an error.

## Summary

We've looked at sending text messages via TCP and UDP and looked at sending file data through TCP.

More advanced uses of networking, especially servers handling connections from multiple clients typically use a multi-threaded approach.

### Topics
1. Launch & Debug Setup
2. App Setup
3. TCP Sockets
4. UDP Sockets
5. Image Syncing

**Source Repository**
* Networking https://github.com/andyguestysj/client-network.git
