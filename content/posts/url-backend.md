+++
title = 'What Happens When You Type a URL into the Search Bar'
date = 2024-10-02T15:59:30-05:00
tags = ["URL", "DNS-resolution", "search bar", "info sec basics"]
draft = false
+++
# What Happens When You Type a URL into the Search Bar

**What is a URL?** A URL, or Uniform Resource Locator, is essentially an address used to pinpoint a specific resource on the internet. URLs can have strings and characters, but they follow a standard format, which includes different components like schemes and subdomains <!--more--> as shown in the image below:

![URL Parts](https://www.hubspot.com/hubfs/URL%20Parts_300-02.jpg)

### Schemes:
1. **http**: HyperText Transfer Protocol, used for transferring hypertext requests and information on the internet.  
   Example: `http://www.example.com`

2. **https**: Secure HyperText Transfer Protocol, a secure version of HTTP using encryption via SSL/TLS for security. We will look at encryption in part 2.  
   Example: `https://www.example.com`

3. **mailto**: Used to open the default mail client and create a new message with the given email address.  
   Example: `mailto:email@address.com`

4. **file**: Used to access local files on a computer.  
   Example: `file:///C:/path/to/file.txt`

These schemes are specified at the beginning of a URL, followed by a colon (`:`) and, in most cases, double slashes (`//`), defining how that URL should be accessed or interpreted.

### Subdomain: 
A subdomain is a prefix added to a website's domain name to separate and organize content. Subdomains can be used for a variety of purposes like separating content that may not be critical to the main website, such as an online store, blog, job board, or support platform.  
Example: If a website's domain name is `yoursite.com`, then `blog.yoursite.com` or `store.yoursite.com` are subdomains.

### Domain/Second-Level Domain:
The second-level domain or domain is essentially the main part of your website's URL.  
Example: `https://yoursite.com` (here `yoursite` is the second-level domain or domain).

### Top-Level Domain:
The top-level domain (TLD) is the extension for a domain, similar to file types like `.pdf`, `.docx`, `.xlsx`. For websites, it could be `.com` (commercial), `.gov` (government), `.edu` (educational), `.us` (United States), or `.fyi`.  
Example: `https://yoursite.com` (here `.com` is the top-level domain).

![DNS Hierarchy](https://www.linode.com/docs/guides/introduction-to-dns-on-linux/DNS-Hierarchy.png)

---

## DNS Resolution/Lookup

Let's take a behind-the-scenes look. After entering our URL, such as `http://secnotes.fyi`, the browser first looks up its cache memory for any data (e.g., IP address) of the URL. If no data is available in the cache, it initiates a process known as **DNS resolution** or **lookup**.

### What is DNS Resolution/Lookup? 
DNS lookup involves searching for the specific IP address of the webserver where the requested resources are hosted. Computers communicate using IP addresses, so when you type a website name, DNS servers translate it into the corresponding IP address.

The process of DNS lookup involves the following steps:

1. **Root Name Server Lookup**  
   The query starts with a lookup at the Root Name Servers, which direct the query to the appropriate Top-Level Domain (TLD) server based on the domain's suffix (e.g., `.com`, `.net`, `.org`).

2. **Top-Level Domain (TLD) Server Lookup**  
   Once the query reaches the correct TLD server (for instance, a `.com` TLD server for domains ending with `.com`), this server doesn't hold the actual IP address but knows the location of the authoritative DNS servers for the specific domain.

3. **Authoritative DNS Server Lookup**  
   The TLD server directs the query to the domain’s authoritative DNS server. This server has the final and exact IP address associated with the domain name.

4. **Caching**  
   After retrieving the IP address, it is sent back to your computer. Along the way, each server involved in the process may cache the IP address for future requests to speed up DNS lookups.

![DNS Resolution](https://sookocheff.com/post/networking/how-does-dns-work/assets/dns-resolution.png)

---

## Network Connection Types and Protocols

Once the IP address is determined, a connection with the webserver is established. There are multiple protocols to establish the connection between your computer and the webserver, such as **TCP**, **UDP**, and **ICMP**.

### TCP (Transmission Control Protocol):
- **Use Case**: Essential for web browsing (HTTP/HTTPS), email (SMTP/POP/IMAP), and file transfers (FTP).
- **Features**: Provides reliable, ordered, and error-checked delivery of data between applications.  
  ![TCP vs UDP](https://i.imgur.com/CdjvCNr.png)

### UDP (User Datagram Protocol):
- **Use Case**: Ideal for streaming video or audio, online gaming, and VoIP (Voice over IP).
- **Features**: Offers connection-less dispatch of datagrams to other hosts. It is faster but lacks reliability.  
  ![UDP vs TCP](https://www.colocationamerica.com/wp-content/uploads/2018/12/udp-tcp.jpg)

### ICMP (Internet Control Message Protocol):
- **Use Case**: Used for diagnostic functions and error reporting in network communication.

---

## HTTP Request and Response Cycle

Once a connection is established, the browser sends an **HTTP request** to the server, which contains methods, headers, and the URL. The server processes this request and sends back an **HTTP response** with the requested data.

### Common HTTP Methods:
- **GET**: Requests data from a specified resource.
- **POST**: Submits data to be processed.
- **PUT**: Updates a specified resource with supplied data.
- **DELETE**: Deletes a specified resource.

### HTTP Response Components:
- **Status Code**: Indicates the result of the request (e.g., 200 OK, 404 Not Found, 500 Internal Server Error).
- **Response Headers**: Provide additional information about the response (e.g., content type, caching).
- **Body**: Contains the actual data, usually in HTML, JSON, or XML format.

![HTTP Request and Response](https://www.researchgate.net/publication/242714677/figure/fig1/AS:644655569973249@1530709273718/Typical-HTTP-response-and-request-headers.png)

---

We got what we needed from the web server, but is it secure? Stay tuned for our next blog to find out.

Thanks for reading!

