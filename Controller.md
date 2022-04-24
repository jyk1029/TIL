## 📒 정의

- **사용자의 요청이 진입**하는 지점(Entry Point)

## ❓ 사용이유

- **역할에 따라 설계를 하고 코딩을하면 개발비용이나 유지보수비용이 대폭 줄어**들기 때문에 Controller를 사용

## 🗒️ 예시

```java
package com.example.hellocontroller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String hello() {
        return "hello";
    }
}
```
