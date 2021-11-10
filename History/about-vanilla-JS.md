- 소개
    - Javascript Engine
        - V8 : Chrome / Opera : 인터프리터 없이 두개의 컴파일러로 구성
        - SpiderMonkey : FireFox : 컴파일러(JIT(Just in Time) )를 사용
        - Trident / Chakra : IE (버전에 따라 다름)
        - ChakraCore : MS Edge
        - Rhino : 모질라 : 기본적으로 인터프리터, 부분적으로 자바 바이트코드로 컴파일
        
    - **엔진은 어떻게 동작하나요?**
        
        엔진이 어떻게 동작하는지 이해하려면 상당한 시간을 쏟아부어야 합니다. 하지만 기본 원리는 다음과 같이 간단합니다.
        
        1. 엔진(브라우저라면 내장 엔진)이 스크립트를 읽습니다(파싱).
        2. 읽어 들인 스크립트를 기계어로 전환합니다(컴파일).
        3. 기계어로 전환된 코드가 실행됩니다. 기계어로 전환되었기 때문에 실행 속도가 빠릅니다.
        
        엔진은 프로세스 각 단계마다 최적화를 진행합니다. 심지어 컴파일이 끝나고 실행 중인 코드를 감시하면서, 이 코드로 흘러가는 데이터를 분석하고, 분석 결과를 토대로 기계어로 전환된 코드를 다시 최적화하기도 합니다. 이런 과정을 거치면 스크립트 실행 속도는 더욱 더 빨라집니다.
        
        - Compiled vs Script
            ![image](https://user-images.githubusercontent.com/70951555/141078001-f1572a0d-14ea-45aa-bfae-9b6755c4e175.png)

            
            - Compile : 코드를 처음부터 끝까지 한번에 다 기계어로 바꿈. 실행시간 빠름
            - Script : Interpreter로 한 줄 한 줄 바꿈. 실행시간이 다소 느림.
            
            ![image](https://user-images.githubusercontent.com/70951555/141078022-da276de9-47de-4ae2-bec7-ed57c7d039ac.png)
            
        
        <aside>
        💻 JavaScript는 Script 언어인데 왜 Compile을 하는가?
        
        </aside>
        
        ⇒ 속도가 빨라지기 때문 !
        
        보통 식과 문으로 나뉘는데 문은 컴파일 과정에서 먼저 데이터 영역으로 들어가고 식은 그 때 그 때 번역됨(interpreter)
        
        ex) 호이스팅, 비동기 등
        
        예전에는 스크립트 언어에 대해 '이 언어는 인터프리터 언어고, 저 언어는 컴파일 언어다' 이야기할수 있었지만 사실 JIT 컴파일러와 VM의 등장이후 어느정도 경계가 흐려졌다고합니다.
        
        [[javascript] 자바스크립트는 컴파일언어인가요 인터프리터 언어인가요?](https://hashcode.co.kr/questions/7560/javascript-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%8A%94-%EC%BB%B4%ED%8C%8C%EC%9D%BC%EC%96%B8%EC%96%B4%EC%9D%B8%EA%B0%80%EC%9A%94-%EC%9D%B8%ED%84%B0%ED%94%84%EB%A6%AC%ED%84%B0-%EC%96%B8%EC%96%B4%EC%9D%B8%EA%B0%80%EC%9A%94)
        
    - 동일 출처 정책(Same Origin Policy)
        
        브라우저 내 탭과 창은 대개 서로의 정보를 알 수 없습니다. 그런데 자바스크립트를 사용해 한 창에서 다른 창을 열 때는 예외가 적용됩니다. 하지만 이 경우에도 도메인이나 프로토콜, 포트가 다르다면 페이지에 접근할 수 없습니다. 이 정책을 피하려면 두 페이지는 데이터 교환에 동의해야 하고, 동의와 관련된 특수한 자바스크립트 코드를 포함하고 있어야 합니다. 
        
        ⇒프로세스와도 같다!
        
    - Javascript의 강점
        - HTML/CSS와 완전히 통합할 수 있음
        - 간단한 일은 간단하게 처리할 수 있게 해줌
        - 모든 주요 브라우저에서 지원하고, 기본 언어로 사용됨
        
    - Javascript 너머의 언어들
        - [CoffeeScript](http://coffeescript.org/)는 자바스크립트를 위한 'syntactic sugar’입니다. 짧은 문법을 도입하여 명료하고 이해하기 쉬운 코드를 작성할 수 있습니다. Ruby 개발자들이 좋아합니다.
        - [TypeScript](http://www.typescriptlang.org/)는 개발을 단순화 하고 복잡한 시스템을 지원하려는 목적으로 '자료형의 명시화(strict data typing)'에 집중해 만든 언어입니다. Microsoft가 개발하였습니다.
        - [Flow](http://flow.org/) 역시 자료형을 강제하는데, TypeScript와는 다른 방식을 사용합니다. Facebook이 개발하였습니다.
        - [Dart](https://www.dartlang.org/)는 모바일 앱과 같이 브라우저가 아닌 환경에서 동작하는 고유의 엔진을 가진 독자적 언어입니다. Google이 개발하였습니다.
        
    
    [JavaScript reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)
    
    [개발자 도구, 기술 설명서 및 코딩 예제](https://docs.microsoft.com/ko-kr/)
