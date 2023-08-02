### Spring에서 http request와 response 로깅 확인 방법

프로젝트 > src > resources > application.properties에서 아래 내용 추가 후 재시작
```
logging.level.org.apache.coyote.http11=debug
```
