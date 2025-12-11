# 🌿 Spring MVC

> 출처: 본 문서는 김영한 강사님의 Spring-MVC 강의를 기반으로 하며,  개인적인 이해 및 해석을 더해 정리한 자료입니다 

### **메시지 국제화 :**
>   - 국제화(i18n)는 애플리케이션을 여러 언어/지역에 맞게 자연스럽게 보여줄 수 있도록 준비하는 과정임
>     - throw new IllegalArgumentException("아이디 또는 패스워드가 잘못되었습니다");
>       - 해당 코드의 설명은에 대해서 영어 사용자들에게는 설명이 불필요해짐
>       - 국제화는 해당 문자열을 외부 파일로 뺴놓고, 상황에 따라 적절한 언어를 선택하도록 만드는 것
>   - **메시지 번들 :**
>     - messages.properties (= login.fail = Login Fail)
>     - messages_ko.properties (= login.fail = 로그인 실패)
>     - messages_en.properties (= login.fail = Login Fail)
>       - 이런식으로 정의를 해놓으면 현재 Locale(= 언어 설정)을 보고 알맞은 프로퍼티로 선택함

### **메시지 소스 설정** 
>   - 스프링 (= Spring Framework)에서의 메시지 설정 (= 기본 스프링 MVC)
>     - 스프링은 기본적으로 MessageSource를 자동으로 등록하지 않음
>       - 그래서 개발자가 직접 Bean으로 등록을 해줘야함
>         ```java
>         -- 예시 (스프링 MVC)
>         @Configuration
>         public class AppConfig {
>       
>           @Bean
>           public MessageSource messageSource() {
>               ResourceBundleMessageSource ms = new ResourceBundleMessageSource();
>               ms.setBasename("messages"); -- message.pro && message_en.pro
>               ms.setDefaultEncoding("UTF-8");
>               return ms;
>           }
>         }

>         - 여기서 중요한 점:
>           - ```setMessage("messages")```라고 하면 ```messages.properties, messages_en.properties``` 같은 파일을 자동으로 탐색함
>           - 기본 인코딩은 ISO-8859-1이라 한글이 깨질수 있으니 UTF-8 필수로 설정
>   - **스프링부트(= Spring Boot)에서의 메시지 설정**
>     - 기본 설정 :
>       - ```classpath:messages.properties```
>       - 아무 작업도 안했을때 해당 기본값들을 적용
>         - ```encoding : UTF-8```
>         - ```basename : messages```