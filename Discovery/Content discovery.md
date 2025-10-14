# important directories
## robots.txt
this is a document that tells search engines which pages they are and aren't allowed to show on their search engine results or ban specific search engines from crawling the website altogether
## sitemap.xml
the sitemap.xml give a list of every file the website owner wishes to be listed on the search engine
# Favicon
A favicon is a small icon displayed in the browser's address bar or tab used for branding a website, sometimes when frameworks are used to build a website a favicon that is a part of the installation is leftover which can give you a clue on what framework is in use
```shell
curl https://<fulldirtofavicon>/favicon.ico | md5sum
```

https://wiki.owasp.org/index.php/OWASP_favicon_database
# HTTP headers
http headers can specify what server has been used to serve the webpage
```
* Trying 10.10.111.225:80...
* TCP_NODELAY set
* Connected to 10.10.111.225 (10.10.111.225) port 80 (#0)
> GET / HTTP/1.1
> Host: 10.10.111.225
> User-Agent: curl/7.68.0
> Accept: */* 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Server: nginx/1.18.0 (Ubuntu)
< X-Powered-By: PHP/7.4.3
< Date: Mon, 19 Jul 2021 14:39:09 GMT
< Content-Type: text/html; charset=UTF-8
< Transfer-Encoding: chunked
< Connection: keep-alive
```