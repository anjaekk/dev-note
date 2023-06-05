### in CLI
```
curl \
--verbose \
--request OPTIONS \
'http://서버host:8000' \
--header 'Origin: http://localhost:3000' \
--header 'Access-Control-Request-Headers: Origin, Accept, Content-Type' \
--header 'Access-Control-Request-Method: GET'
```

### 성공
HTTP/1.1 200 OK

### 실패
HTTP/1.1 405 Method Not Allowed
