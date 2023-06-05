```
curl \
--verbose \
--request OPTIONS \
'http://서버host:8000' \
--header 'Origin: http://localhost:3000' \
--header 'Access-Control-Request-Headers: Origin, Accept, Content-Type' \
--header 'Access-Control-Request-Method: GET'
```
