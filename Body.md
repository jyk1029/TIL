## π ResponseBody

- **μλ° κ°μ²΄λ₯Ό HTTP μμ²­μ body λ΄μ©μΌλ‘ λ§€ν**νλ μ­ν 
- μλ° κ°μ²΄λ₯Ό **HTTP μλ΅ λͺΈμ²΄λ‘ μ μ‘**ν¨

## π RequestBody

- **HTTP μμ²­μ body λ΄μ©μ μλ° κ°μ²΄λ‘ λ§€ν**νλ μ­ν 
- μ΄ μ΄λΈνμ΄μμ΄ λΆμ νλΌλ―Έν°μλ **httpμμ²­μ λ³Έλ¬Έ(body)μ΄ κ·Έλλ‘ μ λ¬**

## β¨οΈ μμ  μ½λ
```java
@Controller
@ResponseBody //@RestController λμ  μ¬μ© κ°λ₯
public class Controller 
{
		// HTTP μμ²­μ λ΄μ©μ Member κ°μ²΄μ λ§€ννκΈ°μν΄ @RequestBody μ΄λΈνμ΄μμ μ€μ 
    @RequestMapping(value="/member/login", method = RequestMethod.POST)
    public MemberResultDto login(@RequestBody Member member) {
    MemberResultDto memberResultDto = memberService.login(member); 
    return memberResultDto;
    }
}
