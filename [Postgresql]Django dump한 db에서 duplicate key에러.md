## 오류메시지
```
message": "duplicate key value violates unique constraint \"userprofile_user_pkey\"\nDETAIL:  Key (id)=(1) already exists.\n
```

dump한 db를 연결하고 단순히 회원가입만 진행하려고 했으나 duplicate key에러 발생



## 해결

Django에서는 친절하게도 app name만 입력하면 sql문을 만들어준다. 전체적용은 안되고 app name을 하나씩 입력해 줘야 한다.
### 쿼리문 만들기
```
python manage.py sqlsequencereset [app name]
```

![](https://images.velog.io/images/anjaekk/post/4965cce4-57b7-4f99-bee4-a1589de7e9f0/image.png)

위처럼 나오는 값들을 db shell창에 입력해준다.
### dbshell 접속
```
python manage.py dbshell
```
> Docker로 연결했을 경우 db 컨테이너에서 psql문을 통해 접속한다.

### sql문 입력
위에 만들어진 sql문을 복사, 붙여넣기 해준다.

그럼 시퀀스 넘버가 자동으로 최대값의 다음으로 지정되어 매겨지게 된다.
