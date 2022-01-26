## 오류메시지
```
message": "duplicate key value violates unique constraint \"userprofile_user_pkey\"\nDETAIL:  Key (id)=(1) already exists.\n
```

dump한 db를 연결하고 단순히 회원가입만 진행하려고 했으나 duplicate key에러 발생


## 해결
```
python manage.py makemigrations --merge
```

git clone받았을 때 기존에 있던 migrations 파일들과 충돌이 있었던 것 같다. 
