##What is Port-Forwarding?

You can translate it lexically, "Give the port to something". but this sentence may be not useful for someone.
So Let's find the specific meaning about it.

Any program using internet communicate with server.
**The computer who can be accessed from other computer is server. The computer who can access to other computer is client.**

Let's say the applications of server are Web server and FTP server.

If we want to access Web server in server computer, we may use the programs like Internet Explorer, FireFox, Chrome.
And Also If we want to access the FTP server in server computer, we may use the programs like AlFTP, SmartFTP.

We use many programs like to access server. but the server didn't know whether the client ask for FTP or Web. So How can server distinguish for client to ask between two server applications. **Port**

Port is number. Normally Port for webserver is 80 and for FTPserver is 21

When the client ask for some resources to server, Server first check the port number, then give request list to process who are wating for before specific port number. In this way, One server can perfrom many things like Multiple server.

###Principle of Port-Forwading
![](http://cfile27.uf.tistory.com/image/2153A04053F01A612735EF)

If you want to ask some resources in 192.168.0.20, you should access first to 61.43.52.108.

Let's say that PC at 192.168.0.20 perform FTP Service
![](http://cfile26.uf.tistory.com/image/2663444453F01A622823A6)

The public server like router doesn't know Which PC perform FTP service. Eventually, the request is failed.

In this situation, **Let the router knows which pc perform some service like FTP** is Port-Forwading.
![](http://cfile29.uf.tistory.com/image/2463534153F01BE62A8891)