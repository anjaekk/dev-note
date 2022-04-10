AWS Aurora RDS 데이터베이스를 생성하도록 하겠다. 테스트용으로 만드는거다보니 요금이 발생하더라도 최소한으로 발생할 수 있도록 했다.

### 1. RDS 데이터베이스 생성
AWS에서 RDS를 검색한 후 대시보드 -> 데이터베이스 생성을 클릭한다. 

![](https://velog.velcdn.com/images/anjaekk/post/eadf1f1c-20ea-4c14-a838-4804a661dc09/image.png)

### 2. 엔진옵션
엔진유형을 Amazon Aurora로 선택하고 에디션에서 Postgresql을 선택한다. 그리고 사용할 Postgresql의 버전을 정한다. 
![](https://velog.velcdn.com/images/anjaekk/post/4ea1151f-710b-4592-8806-4f1f796849e5/image.png)

### 3. 템플릿
난 테스트용이었기 때문에 개발/테스트용으로 템플릿으 선택했다. 둘의 차이는 프로덕션은 다중 AZ(가용 영역)를 지원하고 개발에서는 지원하지않는 차이가 있다.
![](https://velog.velcdn.com/images/anjaekk/post/de30b912-5a8f-4190-bc17-02295513c16e/image.png)


### 4. 설정
db클러스터 식별자에 사용할 클러스트 이름을 넣고(클러스터 이름은 db이름이 아니다. 뒤에 부가설정에 db이름을 따로 설정할 수 있다.) db 접근 아이디인 마스터 사용자이름과 db접근에 사용할 암호를 입력한다.

![](https://velog.velcdn.com/images/anjaekk/post/13c1a483-f745-41b0-9ac3-216fd3e51d37/image.png)

### 5. 인스턴스 클래스
인스턴스가 사용할 클래스를 선택한다. 테스트용이기 때문에 비싼 메모리최적화가 아닌 버스터블로 선택한다. 
![](https://velog.velcdn.com/images/anjaekk/post/5ea3687a-8a19-48d5-8f4a-f8b6c82938fc/image.png)


### 6. 가용성 및 내구성
테스트용이니 다중 AZ배포는 하지 않는다.
![](https://velog.velcdn.com/images/anjaekk/post/07dacc26-e375-4b68-b063-2318d6e57e74/image.png)

### 7. 연결
따로 사용할 vpc와 서브넷이 없다면 default로 설정하도록 한다. 여기서 퍼블릭 액세스가능성을 "예"로 설정해야 외부에서 db접근이 가능해진다. 
![](https://velog.velcdn.com/images/anjaekk/post/80c0d350-5086-439f-a22f-9ca284d8f540/image.png)

### 8. 그 외
최소 단위가 1일이기 때문에 1일로 설정한다. 
![](https://velog.velcdn.com/images/anjaekk/post/4dab8dfb-18bc-40ff-aad4-5da66681e08e/image.png)

일단 도우미든 모니터링이든 추가로 사용하는 것들은 꺼준다..
![](https://velog.velcdn.com/images/anjaekk/post/fd7dfb71-b237-401b-a3cc-f3790bf8695b/image.png)

그 외로 암호화 활성시 마스터키 ID와 KMS(키 관리 서비스) 콘솔을 사용해 만든 후 목록에 나타나게된다. 

### 9. 확인
아래와 같이 라이터 인스턴스가 생성된걸 확인할 수 있다. 
![](https://velog.velcdn.com/images/anjaekk/post/72a7ebab-3078-4052-b47c-2ec4232ab54b/image.png)
작업 -> 읽기추가를 통해 읽기전용 인스턴스를 생성할 수있다. 
![](https://velog.velcdn.com/images/anjaekk/post/c5cef30a-a354-400f-9b1a-65c8432a334a/image.png)

### 10. 접속
연결&보안의 엔드포인트를 통해 접속하도록한다. 
