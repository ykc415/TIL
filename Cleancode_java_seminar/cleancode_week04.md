- 오프라인 강의에 결석하여, 온라인 자료를 보고 정리함.
## 정리 / 궁금한 것 / 더 공부해야할 것
이번 회차에서는 인수테스트 주도 개발(ATDD)이라는 개념이 나온다. 
- 인수테스트란? 
  - 내가 기존에 생각하고 있던 것 : 사용자가 인수해서 프로그램이 제대로 만들어졌는지 테스트하는 것. 요구사항 중심으로 테스트함. 현재 회사 프로젝트에서 해당 단계가 있었으나, 고객사 및 내부 프로젝트팀에 QA관련 인원이 따로 없어서 내가 작성하여 진행함. 해당 테스트케이스는 통합테스트와 큰 차이가 없게 작성했음. [인수테스트](http://www.jidum.com/jidums/view.do?jidumId=563) 이 링크 설명과 비슷하게 파악해서 작성함. 
  - [인수테스트와 테스트를 하는 의미](http://egloos.zum.com/stagile/v/2632377)
    > 테스트는 버그를 확인하기 위한 것이지 실행을 확인하기 위한 것이 아니니까 말이다. 
    - 이 부분은 좀 미묘하다. 
    - 지금까지 내가 경험한 것은 리팩토링할때 테스트케이스가 있으면 안심이 되고, 테스트를 하기 위해서 코드를 작성하다보면, 긴 코드 대신 짧게 로직단위로 나누기가 비교적 쉽다는 거다. 
    - 테스트를 만든다고 해서 버그를 완전히 잡을 수는 없다. 버그가 발생했을때 테스트케이스로 잡을 수는 있겠네. 근데 보통 QA까지 가기 전에 테스트케이스를 이용해서 개발자가 다 테스트하고 넘기지 않나?(테스트케이스 막대 초록색으로 다 되는것 보고 commit) 테스트케이스 빨간 막대 뜨는 것까지 버그라고 하나? (이거 하나도 모르니 모르는 게 줄줄이 나오네. 산넘어 산일세...) 
    - [궁금] 원하는 로직이 제대로 실행되는지를 확인하는게 단위테스트의 목적 아닌가...?
    > 일반적으로 테스트란 인수테스트(사용자들이 정말로 원하는 기능,빼놓을 수 없는 기능)가 포함된 테스트가 진짜 알짜배기 테스트이기 때문에 사용자들이 요구하지 않았거나 다른방향의 테스트를 하기위한 목적이라면 그것은 가짜테스트가 될 수도 있다. 
    - 완전 동의!
    > 분명한 것은 테스트란 고객이 정말로 원하는 기능 , 꼭 필요한 기능, 빈번도가 높은 기능을 위주로 하는 것이 테스트이고 실행확인이 아닌 버그를 확인하기 위한 테스트가 진짜 테스트란 점이다.
    - check*10000! 요즘 가장 많이 하는 삽질 중에 하나가 테스트케이스의 우선순위를 엉망으로 두어서, **기능에 대한 핵심 테스트대신, 내가 생각하기 쉬운 버그 상황에 대한 테스트케이스만 만드는 거 같다.**
- [점진적 소프트웨어 개발 by 테스트 (비공개링크)](https://nextstep.camp/courses/-KxqIISQT-160AGeJrJ_/-KxqLjkLpQyT7h8WcpZJ/lessons/-KxqdgnxnWpWlItOPGZo)
  > 인수 테스트(Acceptance Test) : 시스템 내부 코드를 가능한 한 직접 호출하지 말고 시스템 전. 구간을 테스트해야 한다. 즉, end-to-end 테스트
  - [궁금] 구간 테스트? 어떻게?
- 인수, 통합, 단위테스트 각각 관점이 다름! 
  - 인수 테스트 : **전체 시스템 동작**
  - 통합 테스트 : **변경할 수 없는 코드**를 대상으로 코드가 동작하는가?
  - 단위 테스트 : **객체**의 동작, 객체 이용하기 편한가?

### 더 생각해봐야할 것
- 지금까지 ATDD 이해한 것 : TDD는 단위테스트로 (각 부분의 로직테스트에 집중) 각 단위를 통합해서 기능 테스트를 할때 놓치는 부분이 생김. 이런 한계를 극복하기 위해서 ATDD는 사용자가 필요로 하는 '기능' 테스트를 구현해두고 이를 만족시키기 위해 TDD로 개발한다.
- TDD를 하면서 특히 헤매는 부분을 ATDD를 하면 어떤 부분에서 보완이 될까?
  - 유효성 검사 먼저 실컷하다가 로직을 테스트하는 것을 대충함. (thㅔ상에 나 미쳤나봐...)
  - 각 테스트케이스가 메소드 단위의 로직 테스트로 이루어지다보니 실제 원하는 기능 테스트케이스는 빼놓거나, 전체 기능 테스트를 어떻게 테스트케이스로 쓸지 모르겠음.
  - 이렇게 써놓고 나니 그냥 넘어가고 있는 내가 좀 많이 이상한데... [궁금] 어떻게 해야 이상한 점을 고치지?
- '입력 -> 로직 -> 출력' 을 생각해서 입력값과 출력값을 정의해두고 테스트케이스를 만드는 게 잘 안된다. 엉뚱한 입력값을 넣고 출력값을 원하거나. 
    - 객체로 분석을 못하거나 만들어진 객체를 사용못하는 기분이 든다. 원래 리팩토링하면서 이런 쓸모없는 로직을 깔끔하게 다듬는 걸까? 켄트 벡 TDD 책은 한 번에 이런 거 잘해서 딱히 이런걸 리팩토링 하는 부분은 안나오던데.
    [궁금] 아, 이건 테스트케이스가 아니라 객체로 나누는게 엉망인걸까? 
    - 게다가 method나누면서 테스트케이스가 깨지는게 힘들다. 아래 코드처럼. [궁금] 테스트케이스도 리팩토링해야한다고 했는데 원래 이런 경우가 많이 발생하는게 당연한건가...  
     - 고치기 전 코드  
        
    ```
    void methodOld (List<String> inputs) {
        for (String input : inputs){
          validateInput(input)
          //do something
        }
    }
    ```
  
     - 고친 후 코드
       
    ```
    void methodBetter (List<String> inputs){
        for (String input : inputs){
          methodA(validateInput(input));    
        }
    }
    int methodA (){
        //do something
    }
    ``` 
  
     - 테스트케이스
      
    ```
    @Test
    public void do_something_하는지 확인(){
     // methodOld 테스트
   }
    ```

### 앞으로 볼 것(= 내용이 많거나 지금 내 수준으로는 어려워서 지금 다 이해할 수 없는 것)
- [TDD 이야기, ATDD로 시작하기 by 최범균](http://javacan.tistory.com/entry/TDD-ATDD)
- [테스트 주도 개발로 배우는 객체 지향 설계와 실천(인사이트)](http://www.insightbook.co.kr/book/programming-insight/테스트-주도-개발로-배우는-객체-지향-설계와-실천)
  - 좋다고 해서 사서 읽어봤다가 번역도 어렵고, 내용도 못 알아듣고 지금은 때가 아닌갑다하고 포기한 책. 객체지향도 제대로 모르고 테스트도 모르고 테스트주도개발도 몰라서ㅠㅠ

## 느낀 점 / 단상
- 근데, TDD 도 요구사항 분석이 제대로 되었으면 커버할 수 있지 않나? 훔, 그래도 프로그래머가 놓칠 수 있는 부분을 잡아주는 인수테스트가 있는게 낫겠지. 애초에 프로그래머가 실수 하나도 안하고 한 번에 잘 구현하고 버그도 바로 척척 잡아낸다는 가정 하에 TDD 하는게 아니니까.
