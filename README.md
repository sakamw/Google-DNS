# WHAT HAPPENS WHEN YOU TYPE GOOGLE AND YOU PRESS ENTER?

When you type a URL like "<https://www.google.com>" into a web browser and hit your enter key, there are a lot of things that go on before you finally get some output on your browser.

Fortunately, all these things happen in a split second, so you hardly ever stop to think about them. Before I take the individual steps involved and explain them in detail, let me give you a general overview of everything that goes on within those few microseconds.

1. Your computer sends a request to the `domain name system (DNS)` server which serves as an address book for all domain names. This then sends back the exact IP address of the server which <https://www.google.com> points to.
1. Knowing this IP, your computer then establishes a connection with the server through the IP address. The type of this connection is known as Transmission Control Protocol (TCP) and your computer is able to establish this connection through the Internet Protocol (IP). This whole process is known as a "handshake".
1. If your computer is behind a firewall, the firewall checks to ensure that the particular request you are making is allowed before permitting it. Also, if the server you are trying to access is also behind a firewall, a similar check will be done before you are finally able to connect to the server.
1. After establishing the connection, your browser now sends a request for the webpage using an encryption protocol like Secure Sockets Layer (SSL) or Transport Layer Security (TLS) in order to encrypt the data that will be shared between your computer and the server. This type of encryption is what is responsible for the "s" in **"https"** which also implies that the connection is secure.
1. Companies like Google with high traffic maintain a host of servers and for that matter they have a load balancer that receives most of the requests and sends it to a particular server. The request from your browser will therefore hit the load balancer first which will forward it to a specific server depending on the algorithm used by the load balancer.
1. The server that receives the request then sends a response back to the load balancer which also forwards the response back to your browser. This response will mostly include HTML, CSS, and JavaScript files that makes up Google's homepage.
1. The HTML files returned tells the browser how to render the content of the page. The CSS file tells the browser how to style the content while the JavaScript file adds interactivity to the page.
1. If there is a need for some dynamic content such as Google search results, then the web server will make a request to the application server, which in turn may make a request to a database server to get some data and send it back to the web server. The web server will then include these in the response that it sends back to the browser.
1. Finally, the browser will render the page and display it to you.
