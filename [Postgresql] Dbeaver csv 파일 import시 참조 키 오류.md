Dbeaver에서 csv파일을 import하려는데 계속해서 key오류가 났다.   
결론은 그냥 참조키 무시하고 넣어달라고 체크 하나만 하면 되는데 후 시간을 얼마나 쓴건지 ㅠㅠ

저장할 csv파일을 dbeaver에 csv로 저장해놨다고 가정하고 하겠다.

### 1. 테이블 선택 범위
django migrations을 끝내고 생긴 테이블을 모두 선택한다. (table/밑 데이터들)

### 2. 데이터 가져오기 
데이터 가져오기를 클릭하고 '테이블' 클릭

### 3. auto assign 클릭
`select input objects`단계에서 `auto assign`클릭

### 4. 테이블 mapping
자동으로 맵핑된 테이블 외 Source가 `<none>`으로 되어있는 클릭 후 데이터를 직접 선택해주도록 한다.

### 5. 참조 무시 선택
Data load에서 `Disable referential integrity checks during the transfer` 를 선택해준다. 

### 6. 들어간 데이터 확인
데이터가 잘 들어갔는지 확인한다.
