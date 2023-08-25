# WEB
### SpringBoot에서 application.properties 설정 재정의
> @SpringBootTest(properties = "spring.aop.proxy-target-class=false")   

### Gradle 명령어
> - **클린 및 빌드**   
>   \- ./gradlew clean build   
> - **버전 변경**   
>   \- ./gradlew wrapper --gradle-version=6.5   
> - **버전 확인**   
>   \- gradle -v   

### 서비스 실행 및 프로필 선택 방법
> java -jar -Dspring.profiles.active=[프로필명] [jar명]   
> Ex) java -jar -Dspring.profiles.active=dev web-0.0.1-SNAPSHOT.jar   
> Ex) nohup java -jar -Dspring.profiles.active=dev web-0.0.1-SNAPSHOT.jar & (사용자가 로그아웃해도 백그라운드로 실행)  

### <input> 태그 자동완성 제거
> \- autocomplete="off" 추가    
> ```
> <input type="text" autocomplete="off" />   
> ```

### 툴팁 줄바꿈
> \- 줄바꿈하고자 하는 문장 사이에 엔티티 숫자를 삽인한다.   
> ```
> <span title="줄바꿈이&#10;필요한&#13;문장">툴팁</span>  
> ```
> \- 출력결과  
> 줄바꿈이   
> 필요한   
> 문장   

### <script> 태그의 defer 속성
> \- script 태그의 defer 속성은 페이지가 모두 로드된 후에 해당 외부 스크립트가 실행됨을 명시   
> \- 브라우저가 페이지의 파싱을 모두 끝내면 스크립트가 실행   
> ```
> <script src="/examples/common.js" defer></script>   
> ```
