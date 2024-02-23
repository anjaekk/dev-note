# 피씨 포멧 후 도커파일 이동, 도커 재설치 이후에 생기는 오류
```
error getting credentials - err: exec: "docker-credential-desktop": executable file not found in $PATH, out: ``
```

# 해결방법
### docker config파일의 내용을 변경해준다
~/.docker/config.json 확인
```
{
	"auths": {},
	"credsStore": "desktop",
	"currentContext": "desktop-linux"
}
```

### credsStore => credStore로 변경 (s제거)
