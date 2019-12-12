---
layout: post
title: RESTful - Verbs - Part I
date: 2019-12-12 02:32:20 +0530
description: RESTful API
img: scala.png
tags: [Hackathon]
author: Rajiv Jha
---
December 12, 2019

We will be discussing about 9 HTTP Verbs, which are listed below : 

- GET
- POST
- PUT
- PATCH
- DELETE
- HEAD
- CONNECT
- OPTION
- TRACE

Before moving forward let us understand some common terminology, which is used to represent the property of the methods.

1. Safe

- A HTTP method is said to be safe, if it doesn't alter the state of the server. Only read-only operations are safe.
- Methods like Get, Head, Option.
- All safe methods are idempotent.(GET, HEADS, OPTIONS)
- But All idempotent methdos are not safe.(PUT, DELETE)

2. Idempotent

- if an identical request can be made once or more, several times in a row with the same effect while leaving the server in the same state.
- The method should not have any side effect.
- Implemented correctly, GET, HEADS, OPTIONS, PUT, DELETE are idempotent.
- POST method is not idempotent.

3. Cacheable

- A cacheable response is a http response, that can be cached i.e, stored to be retrieved and used later.
- Saving a new request to the server.
- Not all HTTP response can be cached. 

4. If the method is allowed in HTML Forms or Not.

Let's now move ahead and learn about the HTTP Methods.

GET Method:

- This method request a representation of specified resources.
- Requests using GET should only retrieve data.
- The GET request has body - No
- Successful response has body - Yes
- Safe : Yes
- Idempotent : Yes
- Allowed in HTML forms : Yes
- Cacheable : Yes

POST Method:

- Sends data to the server
- The type of the body of the request is indicated by the content-type header.
- Difference between PUT and POST is : PUT is idempotent & POST is not.
- Successive identical POST may have additional effects, like passing an order several times.
- POST typically is sent via HTML forms.
- POST typically result in the change on the server.
- The content type is selected by putting the adequate string in the enctype attribute of the <form> element or the formenctype attribute of the <input> or <button> elements.
- The POST request has body - Yes
- Successful response has body - Yes
- Safe : No
- Idempotent : No
- Allowed in HTML forms : Yes
- Cacheable : Only if freshness information is included
  




Happy Learning!

Rajiv Jha :)
 
