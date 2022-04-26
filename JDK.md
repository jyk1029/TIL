# JDK

## 📌 정의
- 자바 애플리케이션을 구축하기 위한 **핵심 플랫폼 구성요소**

## 📂 구성
- **apt** : 어노테이션 툴
- **appletviewer** : 웹브라우저 없이 자바 애플릿을 실행하고 디버깅하기 위한 툴
- **javac** : 자바 컴파일러. 자바 소스파일을 바이트코드로 변환
- **java** : javac가 만든 클래스 파일을 해석 및 실행
- **jar** : 서로 관련있는 클래스 라이브러리들과 리소스를 하나의 파일로 묶어주는 툴
- **jdb** : 자바 디버깅 툴
- **JRE(Java Runtime Enviroment)** : Java가 동작하는데 필요한 JVM
    (라이브러리 등 다양한 파일들을 포함한다. Java를 실행하려면 JRE를 설치해야 한다)
- **JVM(Java Virtual Machine)** : Java가 실제로 동작하는 가상 환경
    (이 JVM덕분에 하나의 Java프로젝트를 개발해도 여러 환경에서 원활하게 실행시킬 수 있다)
    
## 📚 종류
1. **Java SE(Java Platform, Standard Edition) :** 표준 자바 플랫폼
    표준적인 컴퓨팅 환경 지원을 하기 위한 자바 가상머신 규격 및 API 집합을 포함한다
    **JavaEE, JavaME :** 구체적인 목적에 따라 자바 SE 기반으로 API를 추가하거나 자바 가상머신 규격 및 API의 일부를 택하여 정의된다
2. **Java EE(Java Platform, Enterprise Edition) :** JavaSE에 웹 어플리케이션 서버에서 동작 기능을 추가한 플랫폼. 이 스펙에 따라 제품을 구현한 것을 웹 어플리케이션 서버(WAS)라 한다. ex. tomcat
3. **Java ME(Java Platform , Micro Edition) :** 제한된 자원을 가진 휴대전화, PDA 등에서 Java 프로그래밍 언어를 지원하기 위해 만든 플랫폼 중 하나
