## ๐ ์ ์

- **์ฌ์ฉ์์ ์์ฒญ์ด ์ง์**ํ๋ ์ง์ (Entry Point)

## โ ์ฌ์ฉ์ด์ 

- **์ญํ ์ ๋ฐ๋ผ ์ค๊ณ๋ฅผ ํ๊ณ  ์ฝ๋ฉ์ํ๋ฉด ๊ฐ๋ฐ๋น์ฉ์ด๋ ์ ์ง๋ณด์๋น์ฉ์ด ๋ํญ ์ค์ด**๋ค๊ธฐ ๋๋ฌธ์ Controller๋ฅผ ์ฌ์ฉ

## ๐๏ธ ์์

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
