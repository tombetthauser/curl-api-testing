![curlin](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fmedia.giphy.com%2Fmedia%2FhbewcRhBwnYvC%2Fgiphy.gif&f=1&nofb=1)

# Testing Local APIs with cURL

Curl (pronounced "curl" but officially typed as "cURL") is a command line utility for transferring data using various network protocols. Curl is accessible on Windows, Linux, and Mac and is an extremely quick tool for checking basic GET and POST requests while developing an API locally. It can be preferable to bulky applications like postman for quick testing and sanity checks.

The name cURL stands for "Client URL". It was first released in 1996 originally being called httpget and then urlget before becoming cURL. The original author and lead developer is the Swedish developer Daniel Stenberg, who created cURL because he wanted to automate the fetching of currency exchange rates for IRC users.

[more meaningless historical context on wikipedia](https://en.wikipedia.org/wiki/CURL)

## Simple GET Requests

Making a GET request is extremely simply and requires no special flags.

```bash
curl http://localhost:5000/api/users
```


## Other Request Types

Making POST requests are pretty simple as well. We can add headers etc with some simple flags. The -X flag specifies a custom request method for communicating with the HTTP server.

```bash
curl -X POST http://localhost:5000/api/users
```


## Sending Data

Using the -d flag allows us to send data with the POST request as in the example below where we send a username and a password field along with their corresponding values.

```bash
curl -d "username=tom&password=hunter2thompson" -X POST http://localhost:5000/api/login
```


## Setting Headers

POSTing with curl’s -d option will include a default header that looks like: Content-Type: application/x-www-form-urlencoded.

To specify the Content-Type in POST request we can use the -H flag. The -H flag can be used to send a specific data type or header as in the following example which sends a JSON object with the request.

```bash
curl -d '{"username": "tom", "password": "hunter2thompson"}' -H 'Content-Type: application/json' http://localhost:5000/api/login
```


## Including Files

We can also sending a file using curl as in the following example that includes a file for form data. This is probably a little further than you would generally go for api testing in the command line. At this point it would make sense to switch into a more robust application like postman.

```bash
curl --form "fileupload=@my-file.txt" http://example.com/resource.cgi
```
