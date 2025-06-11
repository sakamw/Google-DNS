# WHAT HAPPENS WHEN YOU TYPE GOOGLE AND YOU PRESS ENTER?

When you type a URL like "<https://www.google.com>" into a web browser and hit your enter key, there are a lot of things that go on before you finally get some output on your browser.

---

![Process that takes place for searching google.com](image-1.png)

---

## 1. DNS Request

When you visit a website using your browser, it stores DNS information (DNS records) for that domain in its **cache**.
The next time you enter a domain like [google.com](https://www.google.com), the browser first checks its **DNS cache**:

- **If a recent DNS record exists**, the browser uses the cached **IP address** to contact the server directly.
  - This avoids querying a DNS server and speeds up the connection.
- **If no valid cache exists** (or the DNS record has changed), the browser sends a new **DNS request** to resolve the domain to an IP address.

This caching process helps reduce latency and improves browsing speed.

### DNS Lookup Process

The browser sends a request to the local DNS resolver, which is often provided by the internet service provider (ISP). The local DNS resolver checks its cache for the most recent copy of the DNS record for the domain. If it has it, it sends the IP address back to the browser. If the local DNS resolver does not have the most recent copy of the DNS record, it sends a request to a root nameserver. The root nameserver replies with the address of a top-level domain (TLD) nameserver, such as `.com`

- The local DNS resolver sends a request to the TLD nameserver.
- The TLD nameserver responds with the address of the authoritative nameserver for the domain.
- The local DNS resolver sends a request to the authoritative nameserver.
- The authoritative nameserver responds with the IP address for the domain.
- The local DNS resolver sends the IP address back to the browser.
- The browser sends a request to the server at the IP address to retrieve the webpage.

This process may involve additional steps if the DNS record is not found at any of the nameservers or if the DNS record is set up to use a service such as DNS load balancing or content delivery networks (CDN).

## 2. TCP/IP Connection

**TCP (Transmission Control Protocol)** and **IP (Internet Protocol)** are core components of internet communication. Together, they allow a browser and a server to exchange data reliably.

When you visit a website like [google.com](https://www.google.com), the browser uses **TCP/IP** to create a reliable connection with the server.

Here is what happens in details:

1. The browser sends a request to the server using IP to establish a connection.
1. The server receives the request and sends back a message acknowledging the request to establish a connection. This is the handshake process.
1. Once the handshake is complete, the browser can send a request for the webpage it wants to access (in this case, the homepage of [google.com](https://www.google.com)). This request is sent using TCP, which ensures that the request is transmitted reliably and in the correct order.
1. The server receives the request and sends back the HTML code for the homepage of [google.com](https://www.google.com) to the browser. This response is also sent using TCP to ensure reliable transmission.
1. The browser receives the HTML code and uses it to render the webpage on your screen. Any resources (such as images) that the webpage needs are also requested and received using TCP/IP.

## 3. Firewall

A firewall is a security system that monitors and controls incoming and outgoing network traffic based on predetermined security rules. Its primary purpose is to protect a network from external threats, such as hackers and malware.

When you enter a URL like `google.com`, your browser’s request passes through a firewall. The firewall checks whether the request is allowed based on:

1. Source/Destination Rules – e.g., blocking certain IPs or countries.
1. Traffic Type Rules – e.g., allowing only HTTP/HTTPS, or blocking unsafe ports.

If the request follows these rules, it proceeds; otherwise, it's blocked and access is denied.

## 4. HTTPS/SSL

HTTPS (`Hypertext Transfer Protocol Secure`) is a safe version of HTTP, which is used to transmit data on the internet. It encrypts the data sent between your browser and Google's server.

SSL (`Secure Sockets Layer`) and TLS (`Transport Layer Security`) are encryption protocols that ensure the safety of data transmitted over HTTPS.

When your browser establishes a connection with Google's server using HTTPS, your browser and Google's server first agree on the version of SSL/TLS to use and then create a secure, encrypted channel for transmitting the data.

## 5. Load-balancer

A load balancer is a device that distributes incoming network traffic across a group of servers or resources.

Its main goals are to:

- Prevent any single server from being **overloaded**
- **Improve performance**, **scalability**, and **reliability** of applications

Companies like **Google**, which handle **billions of daily visitors**, use many servers to handle traffic.

A **load balancer** ensures traffic is **evenly distributed**, so:

- No server is overwhelmed
- System resources are used efficiently

## 6. Web Server

A web server is a computer program that is responsible for handling requests for web pages from clients (such as a browser trying to access `google.com`). When a client sends a request for a web page to a web server, the server processes the request and returns the appropriate response to the client.

This means that when trying to access google.com, Google's server will receive a request from the load balancer.

## 7. Rendering the Page

Once the browser has received the response from the server, it inspects the resource headers for information on how to render the resource. The Content-Type header above tells the browser it received an HTML resource in the response body. The first GET request returns HTML, the structure of the page.

## Resources Used

1. [LinkedIn](https://www.linkedin.com/pulse/what-happens-when-you-type-googlecom-your-browser-press-sule-bala/)
1. [Mediaum.com](https://medium.com/towards-data-engineering/what-happens-when-you-type-google-com-in-your-browser-and-press-enter-431460a23b42#id_token=eyJhbGciOiJSUzI1NiIsImtpZCI6IjBkOGE2NzM5OWU3ODgyYWNhZTdkN2Y2OGIyMjgwMjU2YTc5NmE1ODIiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL2FjY291bnRzLmdvb2dsZS5jb20iLCJhenAiOiIyMTYyOTYwMzU4MzQtazFrNnFlMDYwczJ0cDJhMmphbTRsamRjbXMwMHN0dGcuYXBwcy5nb29nbGV1c2VyY29udGVudC5jb20iLCJhdWQiOiIyMTYyOTYwMzU4MzQtazFrNnFlMDYwczJ0cDJhMmphbTRsamRjbXMwMHN0dGcuYXBwcy5nb29nbGV1c2VyY29udGVudC5jb20iLCJzdWIiOiIxMDg3Mjg4MjgwNjM2NDg3ODI1MjciLCJlbWFpbCI6InNoYW5td2FuZ2kyMDIwQGdtYWlsLmNvbSIsImVtYWlsX3ZlcmlmaWVkIjp0cnVlLCJuYmYiOjE3NDk2Mzk3OTgsIm5hbWUiOiJJc2FhYyBNd2FuZ2kiLCJwaWN0dXJlIjoiaHR0cHM6Ly9saDMuZ29vZ2xldXNlcmNvbnRlbnQuY29tL2EvQUNnOG9jS09RZTBkT1FaeFNPT1VHcXpRUWU0RW41NTNRaXZZcFF0SWE1UWtHbTVjSV9IYVQ1Zms9czk2LWMiLCJnaXZlbl9uYW1lIjoiSXNhYWMiLCJmYW1pbHlfbmFtZSI6Ik13YW5naSIsImlhdCI6MTc0OTY0MDA5OCwiZXhwIjoxNzQ5NjQzNjk4LCJqdGkiOiI0MjAzMDE0NjkwMDcyZDM5YTFhZjUyNWU5NjBiYzc5MzEyMGE5MjBmIn0.dGsuNfzlOvaqNQkmET7ob4Qy4j6o-CM9oFPXEJlNR95RxCIhHx1NZcFD30CzWDzD0mNsFNLHsARjVEUfk3aXwzwWVBM6fhEXl54GoE0mkmTqCjqVCI6slJbSsZK9EJDjN-9PJt89hZbFaaEA_DCd_fYrxb33SnnXQ1h_6N-6tFwbxhQzf_LqrYkrQufB_t5jByznNd_Ye2CI-4NElGnDCqxGQmTQHSLueaqOeRjFiqcLcv0Bcs5VoY3dY63uBtIEe-r-FIuzqWTVFj9nlMT9sAHNsagAaLfAmzMB5RE85IgAj-CsDPSHNjQ8TxffPtt2ggUSeYU7SRQ2ZAiKDD84zw)
1. [Dr. Ehoneah Obed](https://ehoneahobed.hashnode.dev/what-happens-when-you-type-wwwgooglecom-in-your-browser-and-press-enter#heading-dns-request)
