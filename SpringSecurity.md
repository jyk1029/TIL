## 📌 정의

- Spring 기반의 애플리케이션의 **보안(인증과 권한, 인가 등)을 담당하는 스프링 하위 프레임워크**

## 🔢 처리과정

1. 로그인 요청
2. UserPasswordAuthenticationToken 발급
3. UsernamePasswordToken을 Authentication Manager에게 전달
4. UsernamePasswordToken을 Authentication Provider에게 전달
5. UserDetailsService로 조회할 아이디를 전달
6. 아이디를 기반으로 DB에서 데이터 조회
7. 아이디를 기반으로 조회한 결과 반환
8. 인증 처리 후 인증된 토큰을 Authentication Manager에게 반환
9. 인증된 토큰을 AuthenticationFilter에게 전달
10. 인증된 토큰을 SecurityContextHolder에 저장

![디스패처](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FUOabX%2FbtqEJBBNixH%2FPGDv64FTKaBSLzMiiXkA3K%2Fimg.png)

## ✒ 모듈

![modul](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FAbFLx%2FbtqEJC1tYaJ%2FBDq9cRTqiDarlBa3Z05FoK%2Fimg.png)

### ****[ SecurityContextHolder ]****

- **보안 주체의 세부 정보를 포함**하여 응용프래그램의 **현재 보안 컨텍스트에 대한 세부 정보 저장**
- SecurityContextHolder.MODE_INHERITABLETHREADLOCAL 방법SecurityContextHolder.MODE_THREADLOCAL 방법

### ****[ Authentication ]****

- **현재 접근하는 주체의 정보와 권한을 담는** 인터페이스
- Security Context에 저장
- SecurityContextHolder를 통해 SecurityContext에 접근
- SecurityContext를 통해 Authentication에 접근

```java
public interface Authentication extends Principal, Serializable {
    // 현재 사용자의 권한 목록을 가져옴
    Collection<? extends GrantedAuthority> getAuthorities();

    // credentials(주로 비밀번호)을 가져옴
    Object getCredentials();

    Object getDetails();

    // Principal 객체를 가져옴.
    Object getPrincipal();

    // 인증 여부를 가져옴
    boolean isAuthenticated();

    // 인증 여부를 설정함
    void setAuthenticated(boolean isAuthenticated) throws IllegalArgumentException;
}
```

### ****[ SecurityContext ]****

- **Authentication을 보관**하는 역할
- SecurityContext를 통해 Authentication 객체를 꺼내올 수 있다

### [ UsernamePasswordAuthenticationToken ]

- Authentication을 implements한 AbstractAuthenticationToken의 하위 클래스
- **User의 ID가 Principal 역할, Password가 Credential의 역할**
- 첫 번째 생성자는 인증 전의 객체를 생성, 두번째 생성자는 인증이 완료된 객체를 생성

```java
public class UsernamePasswordAuthenticationToken extends AbstractAuthenticationToken {
    // 주로 사용자의 ID에 해당함
    private final Object principal;
    // 주로 사용자의 PW에 해당함
    private Object credentials;

    // 인증 완료 전의 객체 생성
    public UsernamePasswordAuthenticationToken(Object principal, Object credentials) {
		super(null);
		this.principal = principal;
		this.credentials = credentials;
		setAuthenticated(false);
	}

    // 인증 완료 후의 객체 생성
    public UsernamePasswordAuthenticationToken(Object principal, Object credentials,
			Collection<? extends GrantedAuthority> authorities) {
		super(authorities);
		this.principal = principal;
		this.credentials = credentials;
		super.setAuthenticated(true); // must use super, as we override
	}
}

public abstract class AbstractAuthenticationToken implements Authentication, CredentialsContainer {
}
```

### ****[ AuthenticationProvider ]****

- **실제 인증에 대한 부분** 처리, 인증 전 **Authentication객체를 받아서 인증이 완료된 객체를 반환**
- 아래와 같은 AuthenticationProvider 인터페이스를 구현해서 Custom한 AuthenticationProvider을 작성해서 AuthenticationManager에 등록

```java
public interface AuthenticationProvider {

	// 인증 전의 Authenticaion 객체를 받아서 인증된 Authentication 객체를 반환
    Authentication authenticate(Authentication var1) throws AuthenticationException;

    boolean supports(Class<?> var1);

}
```

### ****[ Authentication Manager ]****

- 인증에 대한 부분은 SpringSecurity의 AuthenticatonManager를 통해서 처리
(실질적으로는 AuthenticationManager에 등록된 AuthenticationProvider에 의해 처리)
- 인증이 성공하면 2번째 생성자를 이용해 인증이 성공한(isAuthenticated=true) 객체를 생성하여 Security Context에 저장
- 인증 상태를 유지하기 위해 세션에 보관하며, 인증이 실패한 경우 AuthenticationException 발생

```java
public interface AuthenticationManager {
	Authentication authenticate(Authentication authentication)
		throws AuthenticationException;
}
```

### ****[ UserDetails ]****

- Authentication객체를 구현한 **UsernamePasswordAuthenticationToken을 생성하기 위해 사용**
- UserDetails 인터페이스를 살펴보면 아래와 같이 정보를 반환하는 메소드를 가지고 있다.
- UserDetails 인터페이스의 경우 직접 개발한 UserVO 모델에 UserDetails를 implements하여 처리하거나 UserDetailsVO에 UserDetails를 implements하여 처리

```java
public interface UserDetails extends Serializable {

    Collection<? extends GrantedAuthority> getAuthorities();

    String getPassword();

    String getUsername();

    boolean isAccountNonExpired();

    boolean isAccountNonLocked();

    boolean isCredentialsNonExpired();

    boolean isEnabled();

}
```

### ****[ UserDetailsService ]****

- UserDetails 객체를 반환하는 단 하나의 메소드를 가지고 있는데, 일반적으로 이를 구현한 클래스의 내부에 UserRepository를 주입받아 DB와 연결하여 처리

```java
public interface UserDetailsService {

    UserDetails loadUserByUsername(String var1) throws UsernameNotFoundException;

}
```

### ****[ Password Encoding ]****

- AuthenticationManagerBuilder.userDetailsService().passwordEncoder() 를 통해 **패스워드 암호화에 사용될 PasswordEncoder 구현체를 지정**

```java
@Override
protected void configure(AuthenticationManagerBuilder auth) throws Exception {
	// TODO Auto-generated method stub
	auth.userDetailsService(userDetailsService).passwordEncoder(passwordEncoder());
}

@Bean
public PasswordEncoder passwordEncoder(){
	return new BCryptPasswordEncoder();
}
```

### ****[ GrantedAuthority ]****

- **현재 사용자(principal)가 가지고 있는 권한**을 의미
- ROLE_ADMIN나 ROLE_USER와 같이 ROLE_*의 형태로 사용(보통 "roles" 이라고 한). GrantedAuthority 객체는 UserDetailsService에 의해 불러올 수 있고, 특정 자원에 대한 권한이 있는지를 검사하여 접근 허용 여부를 결정
