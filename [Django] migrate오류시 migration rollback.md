협업을 진행하다보니 db migration후 붙이면 오류가 나는 경우가 있다. 
이번에 새로운 테이블을 추가하면서 migration오류가 생겼다.

그냥 마이그레이션 파일을 지우고 migrate를 실행할 경우 아래와 같은 오류가 발생할 수 있다. 
```
django.db.migrations.exceptions.NodeNotFoundError: Migration [migration 파일] dependencies reference nonexistent parent node
```
그러니 오류가 발생하기전으로 migrate를 통해 rollback하고 다시 migration을 진행하도록 한다. 


## 에러메세지

```
django.db.utils.ProgrammingError: table [테이블 이름] does not exist
```

## 해결
### 1. app pycache 확인
변경사항이 있었던 app으로 이동해서 pycache를 확인한다.
```
...
0132_auto_20220128_1739.cpython-38.pyc
0133_table.cpython-38.pyc
```
만약 위 두개가 변경사항이라면 삭제해준다.
```
rm 0132_auto_20220128_1739.cpython-38.pyc
rm 0133_table.cpython-38.pyc
```

### 2. migration파일 확인
pycache에 해당하는 번호의 migration도 함께 삭제해준다. 삭제없이 그전 내용으로 rollback할 수도 있다고 하나 그렇게하니 table does not exist오류가 나서 그냥 삭제해줬다.
```
0132_auto_20220128_1739.py
0133_table.py
```
삭제
```
rm 0132_auto_20220128_1739.py
rm 0133_table.py
```

### 3. Rollback
오류가 없었던 파일로 migrate해준다.
```
python manage.py migrate [앱 이름] [migration 번호]
```

### 4. migration
오류없이 위까지 진행 되었다면 
```
python manage.py makemigrations
python manage.py migrate
```
