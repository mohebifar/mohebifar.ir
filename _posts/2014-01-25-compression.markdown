---
layout: post
title:  "gzip contents in web, Advantages and Disadvantages"
date:   2014-01-25 18:01:13
categories: News
---

According to [RFC2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.3) a Http Request may contain an `accept-encoding` header field :
> The Accept-Encoding request-header field is similar to Accept, but restricts the content-codings (section 3.5) that are acceptable in the response.

For example : 

    Accept-Encoding: compress, gzip
    
Why does a browser send this information to the webserver ? Simply it says that the browser is able to decode gzip.
But what are these all for ?

If the webserver handles this capability it will be useful to compress some files, assets (Javascript, CSS) or even your major `text/html` response.

Compressing contents has some advantages and disavantages, so we discuss about that to answer this question : **When should we gzip our responses and when not ?**

**Advantages**
1. Compressing contents helps with decreasing the time it will take for client to download.
2. It saves your bandwidth so it reduces costs ! (Don't wonder if in your country it doesn't matter ! In many countries such as mine, monthly bandwidths are too expensive and this is important to save it !)

**Disadvantages**
1. Compressing contents eats your server's CPU cycles !

The conclusion is there is no disadvantage for your user !

How to enable it in Apache
--------------------------
To compress contents using Apache make sure that `mod_deflate` is enabled.

    LoadModule deflate_module modules/mod_deflate.so

Then add this in httpd.conf :

    <IfModule mod_deflate.c>
      AddOutputFilterByType DEFLATE text/text text/html text/plain text/xml text/css application/x-javascript application/javascript application/json
    </IfModule>

But unfortunately it doesn't cache the static datas and increases the load on your server.
