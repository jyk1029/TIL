## 📌 ResponseBody

- **자바 객체를 HTTP 요청의 body 내용으로 매핑**하는 역할
- 자바 객체를 **HTTP 응답 몸체로 전송**함

## 📌 RequestBody

- **HTTP 요청의 body 내용을 자바 객체로 매핑**하는 역할
- 이 어노테이션이 붙은 파라미터에는 **http요청의 본문(body)이 그대로 전달**

## ⌨️ 예제 코드
```java
@Controller
@ResponseBody //@RestController 대신 사용 가능
public class Controller 
{
		// HTTP 요청의 내용을 Member 객체에 매핑하기위해 @RequestBody 어노테이션을 설정
    @RequestMapping(value="/member/login", method = RequestMethod.POST)
    public MemberResultDto login(@RequestBody Member member) {
    MemberResultDto memberResultDto = memberService.login(member); 
    return memberResultDto;
    }
}
