### 해결

기존에 존재하던 모델이 auto_now_add나 auto_now 필드를 추가하려고 하면 아래와 같은 문구가 생성된다.

```
You are trying to add the field 'created_at' with 'auto_now_add=True' to apptoken without a default; the database needs something to populate existing rows.

 1) Provide a one-off default now (will be set on all existing rows)
 2) Quit, and let me add a default in models.py
```


여기서 1번을 선택해 아래와 같이 나왔을 때 enter 누르면 현재 시점으로 적용 따로 default값을 넣어주고 싶으면 원하는 값 .(다행히 나는 기존 모델에 데이터가 없었음)

```
[default: timezone.now] >>> 
```


### 하지말 것
기존 모델에 default값 넣기
```
created = models.DateTimeField(auto_now_add=True, default=timezone.now())
```
- 오류 생성 migration진행 안됨.
