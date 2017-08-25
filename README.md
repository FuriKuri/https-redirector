# https-redirector
Simple nginx docker images to redirect http to https 

## Usage

Start the docker container and all incomming requests will be responsed with a 301 moved permanently:
```
$ docker run -d -p 8080:80 furikuri/https-redirector

$ curl -v localhost:8080
* Rebuilt URL to: localhost:8080/
*   Trying ::1...
* TCP_NODELAY set
* Connected to localhost (::1) port 8080 (#0)
> GET / HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.54.0
> Accept: */*
>
< HTTP/1.1 301 Moved Permanently
< Server: nginx/1.11.3
< Date: Fri, 25 Aug 2017 13:35:06 GMT
< Content-Type: text/html
< Content-Length: 185
< Connection: keep-alive
< Location: https://localhost/
<
<html>
<head><title>301 Moved Permanently</title></head>
<body bgcolor="white">
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx/1.11.3</center>
</body>
</html>
* Connection #0 to host localhost left intact

# works also with a requested uri
$ curl -v localhost:8080/some/path
*   Trying ::1...
* TCP_NODELAY set
* Connected to localhost (::1) port 8080 (#0)
> GET /some/path HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.54.0
> Accept: */*
>
< HTTP/1.1 301 Moved Permanently
< Server: nginx/1.11.3
< Date: Fri, 25 Aug 2017 13:38:30 GMT
< Content-Type: text/html
< Content-Length: 185
< Connection: keep-alive
< Location: https://localhost/some/path
<
<html>
<head><title>301 Moved Permanently</title></head>
<body bgcolor="white">
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx/1.11.3</center>
</body>
</html>
* Connection #0 to host localhost left intact
```