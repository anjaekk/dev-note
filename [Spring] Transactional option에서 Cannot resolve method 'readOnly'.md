### Spring에서 Transactional option사용시 Cannot resolve method 'readOnly'에러

spring에서 transaction을 read only로 사용하고 싶은 경우 
`@Transactional(readOnly = true)` 어노테이션을 붙이게 되면 Cannot resolve method 'readOnly' 오류가 발생하는 경우가 있다.


### 해결

`import javax.transaction.Transactional;`  => `import org.springframework.transaction.annotation.Transactional;`

위와같이 import 경로를 스프링 프레임워크로 변경해주면 됨.

