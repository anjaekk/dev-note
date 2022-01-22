fastapi로 api구현 후 개발 환경에서는 잘만 나오던 docs..(swagger)가 https로 하니 404에러코드와 함께 나오지 않았다.    
fastapi는 문서가 워낙 잘되어있긴 하지만 이런 예외발생시에 레퍼런스가 많이 없어서 찾다가 open api설정을 하지 않아서 인걸 알게되었다.

### 기존코드
fastapi app을 지정한 부분
```
from fastapi import FastAPI

app = FastAPI()
.
.
.

```

### 변경한 코드
```
from fastapi import FastAPI

app = FastAPI(title='Project title',
            description='Description of your project',
            openapi_url='/api/openapi.json')
.
.
.
```
