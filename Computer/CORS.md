
# CORS(Cross-Origin Resource Sharing)

  CORS는 영문으로 해석하면 교차 출처 리소스 공유의 줄임말로 어떠한 오리진에서 작동하고 있는 웹 어플리케이션이 다른 오리진 서버로의
  
  액세스를 오리진 사이의 HTTP 요청에 의해 허가 할 수 있는 체계라고 할 수 있다.
  
  간단히 얘기 하면 동일한 오리진에서는 허용할 수 있지만 다른 오리진으로는 호출을 할 수 없다는 뜻
  
  체계적으로는 서버에서 응답 헤더에 리소스를 공유하기 위해 헤더를 추가해 허가하는 형태이다.
  
  
  ![image](https://media.vlpt.us/images/josworks27/post/4a53c23c-ca72-4f2c-a7a5-7b53b9df6e6e/CORS_principle.png)
  
# Origin 이란?  
  `오리진과 비슷한 개념으로는 도메인(domain)이 있다. 둘 사이의 구체적인 예로는 아래와 같다.`
  
  - 도메인(domain) : naver.com
  - 오리진(origin) : https://www.naver.com/PORT
  
  `이와 같이 도메인과 오리진의 차이는 프로토콜과 포트번호의 포함 여부이다.`
  
  

# CORS 의 필요성

  __Same-Origin Policy__
  
  웹 시큐리티의 중요한 정책중 하나로 Same-Origin Policy 가 있다. 이는 오리진 사이의 리소스 공유에 제한을 거는 것으로 다음과 같은 위험을 막는 것을 목적으로
  하고 있다.
  
  - XSS(Cross Site Scripting)
    
    유저가 웹 사이트에 접속하는 것으로 정상적이지 않은 요청이 클라이언트(웹 브라우저)에서 실행되는 것을 나타내며,
    Cookie 내에 Session 정보를 탈취 당하는 등의 예시가 있다.
 
 
  - CSRF(Cross-Site Request Forgeries)
    
    웹 어플리케이션의 유저가 의도하지 않은 처리를 웹 어플리케이션엥서 실행되는 것을 나타내며, 원래는 로그인한 유저 밖에 실행할 수 없는 처리가
    멋대로 되는 등의 예시가 있다.
    
    
  
  
  # 참고
  
  [https://velog.io/@josworks27/CORS-%EA%B8%B0%EC%B4%88-%EA%B0%9C%EB%85%90](https://velog.io/@josworks27/CORS-%EA%B8%B0%EC%B4%88-%EA%B0%9C%EB%85%90)
  
  
  
  
  
