[curlin](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fmedia.giphy.com%2Fmedia%2FhbewcRhBwnYvC%2Fgiphy.gif&f=1&nofb=1)

# Testing a Local API with Curl

Curl is a command-line utility that allows users to create network requests. Curl is accessible on Windows, Linux, and Mac. It is an extremely quick tool for checking GET requests but is also fully capable of making other kinds of requests with headers and form data. It can be preferable to bulky applications like postman when doing quick testing and sanity checks on your api.

## Simple GET Requests

Making a GET request is extremely simply and requires no special flags.

```bash
curl https://localhost:5000/api/users
```


## Other Request Types

Making POST requests are pretty simple as well. We can add headers etc with some simple flags. The -X flag specifies a custom request method for communicating with the HTTP server.

```bash
curl -X POST https://localhost:5000/api/users
```


## Sending Data

Using the -d flag allows us to send data with the POST request as in the example below where we send a username and a password field along with their corresponding values.

```bash
curl -d "username=tom&password=hunter2thompson" -X POST https://localhost:5000/api/login
```


## Setting Headers

POSTing with curl’s -d option will include a default header that looks like: Content-Type: application/x-www-form-urlencoded.

To specify the Content-Type in POST request we can use the -H flag. The -H flag can be used to send a specific data type or header as in the following example which sends a JSON object with the request.

```bash
curl -d '{"username": "tom", "password": "hunter2thompson"}' -H 'Content-Type: application/json' https://localhost:5000/api/login
```


## Including Files

We can also sending a file using curl as in the following example that includes a file for form data. This is probably a little further than you would generally go for api testing in the command line. At this point it would make sense to switch into a more robust application like postman.

```bash
curl --form "fileupload=@my-file.txt" https://example.com/resource.cgi
```
