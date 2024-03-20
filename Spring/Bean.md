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

## 어노테이션을 붙이는 클래스

스프링은 약속되어 있는 특정 어노테이션이 붙은 클래스를 자동으로 인식한다.
즉 어노테이션으로 붙여 스프링에서 관리할 수 있도록 어노테이션을 붙여준다.

* @Component
  스프링에서 관리하는 요소라는 의미를 주는 일반적인 어노테이션
  개발자가 직접 작성한 특정한 Class를 Bean으로 등록하기 위함
  @ComponentScan으로 주어진 패키지 내에서 @Component가 적용된 클래스를 식별하고 빈을 생성하여 ApplicationContext에 등록한다.
  (value="") 옵션을 사용하여 특정 Bean ID를 가지게 할 수 있으며 사용하지 않으면 Class 이름을 Camel Case로 변경하여 ID를 가지게 된다.

  ![image](https://github.com/yuyu2323/TIL/assets/45481189/e0ebf5f1-7699-4aa4-af0f-5c3cf2355ecc)

아래 설명하는 어노테이션들은 각 기능을 세분화하여 가독성을 높이고, 어떠한 역할을 가지는지 명확하게 알 수 있도록 하는데 의미가 있다.

* @Controller    
  Spring MVC에서 컨트롤러 역할을 하는 클래스를 표현하는 어노테이션
  전통적인 Controller의 외부 인터페이스 또는 View에 표시할 템플릿을 반환하는데 역할이 있다.

* @Service    
  Spring MVC에서 서비스의 역할을 하는 클래스를 표현하는 어노테이션
  Controller에서부터 유입된 요청을 개발자가 의도한 로직이 수행되고 다시 Controller로 반환하는 역할을 한다.

* @Repository    
  레포지토리 역할을 하는 클래스를 표현하는 어노테이션
  DB나 I/O 접근을 하기위해 사용되는 인터페이스 역할을 한다.

