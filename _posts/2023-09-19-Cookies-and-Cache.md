---
layout: post
title: Cookies? Cache?
date: 2023-09-19 20:10:20 +0900
description: Cookies and Cache # Add post description (optional)
img: Candc.svg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Web, Cookies, Cache]
---

<h1>Why are Cookies on the Web Called Cookies?</h1>

Cookies on the web are called "cookies" because the term is an analogy drawn from the world of physical cookies. When web cookies were first introduced, their behavior was likened to that of physical cookies, which people use to store and retrieve small pieces of data.

Here's the original analogy to explain this naming:

1. **Interaction**: When you visit a website and perform actions like logging in, adding items to a shopping cart, or customizing settings, the website needs a way to remember these actions and who you are. Similarly, when you order something in a bakery, the server needs a way to remember your order.

2. **Data Storage**: In a bakery, your order may be written on a piece of paper or a notepad. On the web, websites use cookies to store and retrieve data related to your interactions.

3. **Persistence**: Just as you take your physical cookie with you when you leave the bakery, web cookies persist across different interactions with a website. They are stored on your computer, and when you return to the same website, the website can access and use the stored data.

4. **Expiration**: Like physical cookies, web cookies can have an expiration time. Some cookies are session cookies, which are deleted when you close your browser (similar to finishing your cookie), while others can be persistent and last for a specified period.

So, web developers chose the term "cookie" as an analogy to describe the way web cookies function, helping websites remember user interactions and data between visits. Web cookies play a crucial role in enhancing the web browsing experience and managing user sessions, much like how physical cookies store and remember your preferences at a bakery.

<h1>Diffrence Between Cookies and Cache</h1>

Cookies and cache are two distinct concepts in web technology, each serving different purposes and operating in different ways. Here are the key differences between cookies and cache:

1. **Purpose**:

   - **Cookies**: Cookies are primarily used for maintaining state and session information between a web server and a web browser. They store small pieces of data on the client-side (user's device) to track user interactions, manage user sessions, personalize user experiences, and store user preferences.

   - **Cache**: Cache is used to store copies of web resources (e.g., web pages, images, stylesheets, scripts) temporarily on the client-side or on intermediate servers (e.g., proxy servers, Content Delivery Networks - CDNs). The purpose of caching is to improve web page loading speed and reduce server load by serving previously retrieved resources from a local cache rather than fetching them from the server again.

2. **Location**:

   - **Cookies**: Cookies are stored on the client-side, usually within the user's web browser. Each website can only access its own cookies, and cookies are sent back to the server with every HTTP request for a specific domain.

   - **Cache**: Cache can be stored in various locations:
     - **Browser Cache**: Caches resources on the user's device.
     - **Proxy Cache**: Caches resources on intermediate proxy servers.
     - **CDN Cache**: CDNs cache resources on their servers distributed across different geographical locations.

3. **Content**:

   - **Cookies**: Cookies typically store textual or small binary data, such as user IDs, session IDs, user preferences, and tracking information. They are used for maintaining user-related data.

   - **Cache**: Cache stores complete web resources, such as HTML pages, images, CSS files, JavaScript files, and more. These resources are static and are used to speed up the loading of web pages by serving them from local storage.

4. **Management**:

   - **Cookies**: Cookies are managed by both the server and the client-side JavaScript code. Web developers can create, read, update, and delete cookies from the client-side or server-side scripts.

   - **Cache**: Cache management is typically handled by the browser or intermediate servers. Browsers automatically decide whether to use cached resources based on HTTP headers, like "Cache-Control" and "Expires," and can clear the cache as needed.

5. **Data Lifecycle**:

   - **Cookies**: Cookies have a specified expiration time, and some are session cookies that expire when the user closes the browser. Persistent cookies can have longer lifetimes.

   - **Cache**: Cached resources have a "time-to-live" (TTL) specified in their headers, after which they expire and are fetched anew from the server. Cached resources can be invalidated and replaced by newer versions based on cache-control policies.

In summary, cookies and cache serve different purposes in web technology. Cookies are used for managing user-related data and sessions, while cache is used for storing and speeding up the retrieval of web resources. Both play crucial roles in enhancing web performance and user experiences.