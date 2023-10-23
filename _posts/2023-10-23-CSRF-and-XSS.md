---
layout: post
title: CSRF VS XSS Attacks - What is the Differences?
date: 2023-10-23 20:10:20 +0900
description: CSRF VS XSS Attacks # Add post description (optional)
img: hacker.jpeg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Web-develope, CSRF, XSS]
use_math: true
---

Cross-Site Request Forgery (CSRF) and Cross-Site Scripting (XSS) are both security vulnerabilities that can affect web applications.

**Cross-Site Request Forgery (CSRF):**

CSRF is an attack in which an attacker tricks a user into performing actions on a web application without their knowledge or consent. This is done by exploiting the user's authenticated session in the application. Here's how it works:

1. The attacker creates a malicious website or embeds malicious code in a legitimate website.
2. The victim, who is logged into a targeted web application, visits the malicious website.
3. The malicious website sends unauthorized requests (usually HTTP requests) to the targeted application on behalf of the victim.
4. If the victim's session is still active, the application processes these requests, effectively performing actions as if initiated by the victim.

**Cross-Site Scripting (XSS):**

XSS is an attack in which an attacker injects malicious scripts into web pages viewed by other users. These scripts can execute within the context of a victim's browser and can steal data, manipulate the web page's content, or perform other malicious actions. There are three main types of XSS attacks:

1. **Stored XSS:** The malicious script is stored on the server and served to users when they visit a particular web page.

2. **Reflected XSS:** The malicious script is embedded in a URL and is reflected off a web server, executing when a victim clicks on a specially crafted link.

3. **DOM-based XSS:** The attack takes place in the Document Object Model (DOM) of the web page, often manipulating the client-side code without necessarily interacting with the server.

Now, let's create a comparison table to highlight the differences between CSRF and XSS:

| Aspect                  | CSRF                                   | XSS                                    |
|-------------------------|---------------------------------------|---------------------------------------|
| Attack Type             | Exploits the trust a website has in a user's browser. | Exploits the trust a user has in a website. |
| Attack Objective        | Initiates unauthorized actions on behalf of the victim. | Executes malicious scripts within the victim's browser. |
| Victim's Involvement    | Victim is usually unaware of the attack. | Victim actively interacts with a compromised web page. |
| Targeted Component      | Targeted web application's server-side actions. | Victim's browser and client-side scripts. |
| Delivery Mechanism      | Utilizes the victim's authenticated session. | Injects malicious code into web pages. |
| Types                   | Single request, multi-request (e.g., changing account settings). | Stored, reflected, DOM-based. |
| Mitigation Strategies   | Anti-CSRF tokens, Same-Site cookies, Referer header checks. | Input validation, output encoding, Content Security Policy (CSP). |

In summary, CSRF is primarily about tricking a user into performing actions on a web application without their knowledge, while XSS involves injecting malicious scripts into web pages to manipulate or steal data within a victim's browser. Both vulnerabilities are serious and should be mitigated to ensure the security of web applications.