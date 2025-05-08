+++
title = 'Part2 - What Happens When You Type a URL into the Search Bar'
date = 2025-05-07T22:28:35-05:00
draft = true
+++


After the web browser renders the response and the user begins interacting with the page, several additional processes can occur based on user actions and web page scripts. These interactions can trigger new cycles of requests and responses, influencing both the user experience and the server workload. Throughout this process, additional resources such as images, CSS files, and JavaScript files referenced in the HTML may be requested separately via further HTTP requests, following the same cycle of request and response. This iterative process ensures that all elements of the webpage are properly loaded and displayed, offering the user a complete and functional web experience.


What do we mean by secure? If you're using HTTP, anyone watching your network can see everything you send or receive because it's not hidden—it's plain text. To fix this, we use something called TLS (Transport Layer Security). Before TLS, there was SSL, but it had problems and is no longer recommended. TLS keeps the connection between your browser and the website safe by encrypting the data so others can’t read or change it.

## How the Web “Remembers” You

HTTP is **stateless**—every request is a brand-new conversation.  
If you log in and then refresh, the server normally forgets who you are.


### Cookies to the Rescue

1. **Login → `Set-Cookie`**  
   - After you enter your username + password, the server verifies them.  
   - It then creates a random **session ID** (a long unique string) and returns it in a small text file called a **cookie**.  
   - Your browser stores the cookie.

2. **Next Request → Cookie Returns**  
   - On every new click or refresh, the browser automatically adds that cookie to the request.  
   - The server looks up the session ID, says *“Oh, that’s the same user—still logged in,”* and keeps you authenticated.

> **Note:**  
> The cookie normally holds *only* the session ID—no passwords or private data.  
> All personal details live on the server, linked to that ID.


### Logging Out & Expiration

* **Logout button:** Deletes the cookie in the browser **and** erases the matching session on the server.  
* **Expiry time:** Cookies auto-expire (e.g., after 30 min of no activity or when the tab closes).

**TL;DR**  
Cookies (or tokens) give stateless HTTP a memory, letting websites keep you logged in, store settings, and maintain shopping carts—while safety flags and good logout practices keep your session secure.
