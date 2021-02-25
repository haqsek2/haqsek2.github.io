---
title: Directory Traversal Vulnerability In TP-Link Wireless N Router WR940N
published: true
---

Before getting started I want to define directory traversal for those who don’t know about it, if you already know about this vulnerability you can just skip this introductory section.

>Directory Traversal also known as path traversal is a web security vulnerability in which an attacker can read arbitrary files on the server or in some cases attacker might can write or modify files on the server. So ultimately attacker can take control of the server.

Now lets start the most interesting section of this write-up

## how did I found this vulnerability?
One day I got mail from a news agency with this interesting title **“Thousands of home routers hacked — what can you do?”**. It might not be interesting for many of you, but for me as an security enthusiast I decided to test my personal home router.

>If you are really a Hacker! then give it a try

Whenever I test any application I first look for common vulnerabilities, I tested for authentication and It was pretty secure. Then I decided to test for LFI and RFI and it was that moment when I realized that this router is not secure at all.

I used this simple payload **”../../../etc/shadow”** to observe how the router will react and I was shocked to see this:

![](https://raw.githubusercontent.com/haqsek2/haqsek2.github.io/main/assets/1_kmNhb8j-258uD6wIMjNkQw.png)

I was able to read the system files by login into the router panel. So I was curious that can I read these files without authentication? guess what happened.

As you can see in the request there is no authentication header present, it means an unauthenticated user can also exploit this vulnerability. Which makes this more dangerous.

**Note: I found this vulnerability on TP-Link Wireless N Router WR940N with the hardware version “
WR940N” and firmware version “ 3.12.8”**

