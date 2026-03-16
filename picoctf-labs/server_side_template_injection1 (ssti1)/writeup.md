# Overview
This challenge involved exploiting a server-side template injection (ssti) vulnerability in a Flask/Jinja2 web application. The goal was to manipulate the template engine to execute Python code on the server and retrieve the flag.

## Tools Used
- Burp Suite
- Web Browser
- PicoCTF Web Challenge Environment

## Steps
### 1. Initial Reconnaissance

Upon visiting the challenge website, a simple form was presented allowing users to submit text to be displayed as an announcement.
![Initial Website](screenshots/02_website_to_exploit.png) 

The form accepted user input which appeared to be processed by the server
![Hello World Input](screenshots/03_input_hello_world.png)

clicking 'OK' produced the following:
![Hello World Response](screenshots/04_hello_world_response.png)

### 2. Intercepting the Request
Using Burp Suite, the HTTP request was intercepted when submitting input through the form. The request contained a parameter named 'content'.
![Burp Suite Post Request Interception](screenshots/05_burp_suite_post_request_interception.png)

Sending to repeater and creating different requests suggested that the server was taking user input and creating the webpage content based on what the user sends. 
Several types of input were tested, including a string ("Hello World") and a numeric value (3.0) and another string with special characters("test;ls"), to observe how the server processed input. 
![Burp Suite Send to Repeater](screenshots/06_burp_suite_send_to_repeater.png)

![Burp Suite Change Content to Float](screenshots/07_burp_suite_change_content_to_float.png)

![Burp Suite Change Content to Special Characters](screenshots/08_burp_suite_change_content_to_special_characters.png)

### 3. Testing for Template Injection
To determine whether the application was vulnerable to Server-Side Template Injection (SSTI), a simple arithmetic expression was submitted as input.
![Burp Repeater Test for SSTI](screenshots/09_burp_repeater_test_for_ssti.png)

In template engines such as Jinja2, expressions inside double curly braces ({{}}) are evaluated by the server before the page is rendered.

If the server treated this input as normal text, the response would display:
```
{{7*7}}
```
However, the server returned
```
49
```
Since 7 x 7 = 49, this indicates that the expression was executed by the template engine rather than being displayed as plain text.

This confirmed that the application was rendering user input within a template engine, demonstrating the presence of a Server-Side-Template Injection (SSTI) vulnerability.

### 4. Payload execution
After confirming that template expressions were evaluated, the vulnerability was used to execute a system command.

The following payload was sent through Burp Repeater:
![SSTI Directory Listing](screenshots/10_ssti_directory_listing.png)

This payload accesses Python's os module through Jinja's global objects and executes the ls command on the server.

The response returned a list of files in the appplication directory.

This confirmed that the SSTI vulnerability allowed command execution and revealed the presence of the flag file. 

Executing the command
### 5. Retrieving the flag

Executing the command 
```
cat flag
```
allowed the retreval of the flag

![SSTI Cat Flag Output](screenshots/11%20ssti_cat_flag_output.png)
