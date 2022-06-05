## 📌 정의

- **익명구현 객체**를 생성

## 📎 사용 이유

1. 코드 간결
2. 가독성 UP

## 💻 기본 구조

`A a = (매개값) -> { 구현코드 };`

## 🖥 작성 예제

#### 매개변수가 없고 리턴값이 없는 람다식

```java
public class Execute {
    public static void main(String[] args) {
        //객체 선언
        JavaCoding jc;

        //{} 실행코드 뒤에 세미콜론(;)을 붙여야한다
        jc = () -> {
            System.out.println("Rollin' Rollin' Rollin' Rollin'");
        };
        jc.nowCoding();

        // {} 실행코드가 1줄인경우 {} 생략가능
        jc = () -> System.out.println("Rollin' Rollin' Rollin' Rollin'");
        jc.nowCoding();
    }
}
```

#### 매개변수가 있고 리턴값이 없는 람다식

```java
public class Execute {
    public static void main(String[] args) {
        //객체 선언
        JavaCoding jc;
        String str;

        jc = (a) -> {
            System.out.println(a+ " Rolling in the deep");
        };
        str = "하루가 멀다하고";
        jc.nowCoding(str);

        //람다식 바디{}를 생략하고 한 줄에 작성하기
        jc = (a) -> System.out.println(a+ " Babe just only you");
        str= "기다리고 있잖아";
        jc.nowCoding(str);

        //매개변수가 1개인 경우 () 생략할 수 있음
        jc = a -> System.out.println(a+ " 기다리고 있어요");
        jc.nowCoding("온종일 난 그대 생각에");
    }
}
```

#### 매개변수가 없고 리턴값이 있는 람다식

```java
public class Execute {
    public static void main(String[] args) {
        //객체 선언
        JavaCoding jc;

        String str1 = "그 날을 잊지 못해 baby";
        String str2 = "날 보며 환히 웃던 너의 미소에";
        String str3 = "홀린 듯 I'm fall in love";

        jc = () -> {
            return str1;
        };
        System.out.println(jc.nowCoding());

        jc = () -> { return str2; };
        System.out.println(jc.nowCoding());

        //실행코드가 return 만 있는 경우 {}와 return문 생략가능
        jc = () -> str3;
        System.out.println(jc.nowCoding());
    }
}
```

#### 매개변수가 있고 리턴값이 있는 람다식

```java
public class Execute {
    public static void main(String[] args) {
        //객체 선언
        JavaCoding jc;

        String str1 = " 너의 생각뿐이야";
        String str2 = " 미치겠어";
        String str3 = " 보고 싶어";

        jc = (s) -> {
            return s+ str1;
        };
        System.out.println(jc.nowCoding("온통"));

        jc = (s) -> { return s+ str2; };
        System.out.println(jc.nowCoding("나도"));

        jc = s -> s+ str3;
        System.out.println(jc.nowCoding("너무"));
    }
}
```

## 👍 장점

- 효율적인 람다 함수의 사용으로 불필요한 루프문의 삭제가 가능하며, 함수의 재활용이 용이
- 필요한 정보만을 사용하는 방식을 통한 성능 향상
- 일반적으로 다중 cpu를 활용하는 형태로 구현되어 병렬 처리에 유리
- 코드가 간결해져 개발자의 의도가 명확히 드러나므로 가독성이 향상

## 👎 단점

- 이론상 단순하게 모든 원소를 전부 순회하는 경우 람다식이 조금 느릴 수 있음
- 디버깅 시 함수 콜 스택 추적이 다소 어려움
- 지나치게 남발하면 코드가 이해하기 어렵고 지저분해짐
- 람다를 사용하여 만든 무명함수는 재사용이 불가능함
