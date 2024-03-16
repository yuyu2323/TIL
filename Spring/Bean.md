# Spring bean
## Bean
Spring IoC(Inversion Of Contorl, 제어의 역전) 컨테이너가 관리하게 되는 자바 객체를 뜻한다.
> ### IoC
> + Inversion of Control의 줄임말로 한글로 번역하면 제어의 역전 객체의 호출
> + 객체 생성의 특별한 관리(각 객체를 직접 생성하고 조작하거나 호출 하는 행위) 위임을 개발자가 직접하는 것이 아닌 <b>객체의 생명주기 컨트롤을 다른 주체에게 넘기는 것</b>
> + main 메소드에서 시작하여 개발자가 정한 순서대로 실행되는 개념이 아닌 <b>Spring의 프레임워크 내에 필요한 컴포넌트를 개발하고 조립하는 방식</b>
> + 즉 프로그램 내부의 프레임워크 내부에서 결정된 대로 생성과 호출이 일어난다.

Spring은 하나 이상의 Bean을 가지게 되며 빈은 컨테이너에 등록된 인스턴스화 된 객체이다. 기본적으로 @Bean 어노테이션을 통해 스프링 컨테이너에 Bean이 등록된다. 사용의 가장 큰 목적은 Spring 간 객체의 의존관계를 관리하는 것에 있다.
 
## Bean 의존성 주입 DI
객체가 사용하는 의존 객체를 직접 생성(new)하는 것이 아닌 스프링 컨테이너에 주입 받아 사용하는 것
**스프링 컨테이너의 객체 정보를 가져온다**
필드 주입 방식, Setter 주입 방식, 생성자 주입 방식 등이 있다.

## Bean 등록
* 필드 주입 방식
```
  @Autowired
  private Repository repository;
```
@Autowired 어노테이션을 사용하여 고정적으로 주입한다.

* Setter 주입 방식
```
private Repository repository;

public void setRepository(Repository repository) {
    this.repository = repository;
}
```

* 생성자 주입 방식
```
@Service
public class Service {
		private final Repository repository;
		
		@Autowired
		public Service(Repository repository) {
		    this.repository = repository;
		}
```
