## π μ μ

- **μ΅λͺκ΅¬ν κ°μ²΄**λ₯Ό μμ±

## π μ¬μ© μ΄μ 

1. μ½λ κ°κ²°
2. κ°λμ± UP

## π» κΈ°λ³Έ κ΅¬μ‘°

`A a = (λ§€κ°κ°) -> { κ΅¬νμ½λ };`

## π₯ μμ± μμ 

#### λ§€κ°λ³μκ° μκ³  λ¦¬ν΄κ°μ΄ μλ λλ€μ

```java
public class Execute {
    public static void main(String[] args) {
        //κ°μ²΄ μ μΈ
        JavaCoding jc;

        //{} μ€νμ½λ λ€μ μΈλ―Έμ½λ‘ (;)μ λΆμ¬μΌνλ€
        jc = () -> {
            System.out.println("Rollin' Rollin' Rollin' Rollin'");
        };
        jc.nowCoding();

        // {} μ€νμ½λκ° 1μ€μΈκ²½μ° {} μλ΅κ°λ₯
        jc = () -> System.out.println("Rollin' Rollin' Rollin' Rollin'");
        jc.nowCoding();
    }
}
```

#### λ§€κ°λ³μκ° μκ³  λ¦¬ν΄κ°μ΄ μλ λλ€μ

```java
public class Execute {
    public static void main(String[] args) {
        //κ°μ²΄ μ μΈ
        JavaCoding jc;
        String str;

        jc = (a) -> {
            System.out.println(a+ " Rolling in the deep");
        };
        str = "νλ£¨κ° λ©λ€νκ³ ";
        jc.nowCoding(str);

        //λλ€μ λ°λ{}λ₯Ό μλ΅νκ³  ν μ€μ μμ±νκΈ°
        jc = (a) -> System.out.println(a+ " Babe just only you");
        str= "κΈ°λ€λ¦¬κ³  μμμ";
        jc.nowCoding(str);

        //λ§€κ°λ³μκ° 1κ°μΈ κ²½μ° () μλ΅ν  μ μμ
        jc = a -> System.out.println(a+ " κΈ°λ€λ¦¬κ³  μμ΄μ");
        jc.nowCoding("μ¨μ’μΌ λ κ·Έλ μκ°μ");
    }
}
```

#### λ§€κ°λ³μκ° μκ³  λ¦¬ν΄κ°μ΄ μλ λλ€μ

```java
public class Execute {
    public static void main(String[] args) {
        //κ°μ²΄ μ μΈ
        JavaCoding jc;

        String str1 = "κ·Έ λ μ μμ§ λͺ»ν΄ baby";
        String str2 = "λ  λ³΄λ©° νν μλ λμ λ―Έμμ";
        String str3 = "νλ¦° λ― I'm fall in love";

        jc = () -> {
            return str1;
        };
        System.out.println(jc.nowCoding());

        jc = () -> { return str2; };
        System.out.println(jc.nowCoding());

        //μ€νμ½λκ° return λ§ μλ κ²½μ° {}μ returnλ¬Έ μλ΅κ°λ₯
        jc = () -> str3;
        System.out.println(jc.nowCoding());
    }
}
```

#### λ§€κ°λ³μκ° μκ³  λ¦¬ν΄κ°μ΄ μλ λλ€μ

```java
public class Execute {
    public static void main(String[] args) {
        //κ°μ²΄ μ μΈ
        JavaCoding jc;

        String str1 = " λμ μκ°λΏμ΄μΌ";
        String str2 = " λ―ΈμΉκ² μ΄";
        String str3 = " λ³΄κ³  μΆμ΄";

        jc = (s) -> {
            return s+ str1;
        };
        System.out.println(jc.nowCoding("μ¨ν΅"));

        jc = (s) -> { return s+ str2; };
        System.out.println(jc.nowCoding("λλ"));

        jc = s -> s+ str3;
        System.out.println(jc.nowCoding("λλ¬΄"));
    }
}
```

## π μ₯μ 

- ν¨μ¨μ μΈ λλ€ ν¨μμ μ¬μ©μΌλ‘ λΆνμν λ£¨νλ¬Έμ μ­μ κ° κ°λ₯νλ©°, ν¨μμ μ¬νμ©μ΄ μ©μ΄
- νμν μ λ³΄λ§μ μ¬μ©νλ λ°©μμ ν΅ν μ±λ₯ ν₯μ
- μΌλ°μ μΌλ‘ λ€μ€ cpuλ₯Ό νμ©νλ ννλ‘ κ΅¬νλμ΄ λ³λ ¬ μ²λ¦¬μ μ λ¦¬
- μ½λκ° κ°κ²°ν΄μ Έ κ°λ°μμ μλκ° λͺνν λλ¬λλ―λ‘ κ°λμ±μ΄ ν₯μ

## π λ¨μ 

- μ΄λ‘ μ λ¨μνκ² λͺ¨λ  μμλ₯Ό μ λΆ μννλ κ²½μ° λλ€μμ΄ μ‘°κΈ λλ¦΄ μ μμ
- λλ²κΉ μ ν¨μ μ½ μ€ν μΆμ μ΄ λ€μ μ΄λ €μ
- μ§λμΉκ² λ¨λ°νλ©΄ μ½λκ° μ΄ν΄νκΈ° μ΄λ ΅κ³  μ§μ λΆν΄μ§
- λλ€λ₯Ό μ¬μ©νμ¬ λ§λ  λ¬΄λͺν¨μλ μ¬μ¬μ©μ΄ λΆκ°λ₯ν¨
