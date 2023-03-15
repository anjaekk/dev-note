현재 사용하고 있는 gradle 버전에 따른 lombok 의존성 추가 방식이 다름

### 해결
[project lombok](https://projectlombok.org/setup/gradle) 에서 gradle 버전에 맞게 의존성 추가할 것

나는 gradle 7.6버전이라 아래와 같이 추가
```
repositories {
	mavenCentral()
}

dependencies {
	compileOnly 'org.projectlombok:lombok:1.18.26'
	annotationProcessor 'org.projectlombok:lombok:1.18.26'
	
	testCompileOnly 'org.projectlombok:lombok:1.18.26'
	testAnnotationProcessor 'org.projectlombok:lombok:1.18.26'
}
```
