# Cookies   

## Question 1
What if any are the acess restricitions for websites when dealing with cookies? 

## Answer 1

Only the website domain that created a cookie can access it. A cookie has arestricted access to only the site that created it (specifically, only the sites with matching domain).

## Question 2

What is a solution to cookies storing too much data and becoming too large in size?

## Answer 2

Store only an id, and the data elsewhere. The unique if would identify the client, and the data could be stored on the server. 

## Question 3

How does a server set a cookie on a client browser? 

## Answer 3

The server sends cookie-data in the HTTP response header.

## Question 4

How do we prevent a user's cookie from being stolen by a 'man-in-the-middle'? 

## Answer 4

Enable HTTPS for our site. Only by encrypting all communications between the client and server can we protect a user's cookie data from being stolen by a third party listening in. However, it's still possible that a bad extension or other malware on the user's computer can steal the user's cookie (or, malware on out servers).

## Question 5

Which of the following would not be a usage of HTTPS cookies? 

## Answer 5

Redirection


