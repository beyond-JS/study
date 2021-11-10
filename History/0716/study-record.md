- 김수연
    
    [실행 컨텍스트](https://alveloper.oopy.io/12124968-4d70-4dbd-8a73-75792d7c72e7)
    
- 윤수진
    - 자바스크립트 클래스
        - fields : 변수
        
        - methods : 함수
        
        ```jsx
        class {
        	변수
        	함수
        }
        ```
        
        클래스 : 몬스터
        
        객체 : 슬라임1, 슬라임2...
        
        constructor : 생성자
        
        - private / public / protected
            
            private : 외부에서 접근 못함.
            
            public : 외부에서 접근할 수 있다.
            
            protected : 외부에서 접근 못함. 단, 상속받은 자식클래스에서 부모 클래스에 접근할 수 있음.
            
        
        public
        
        #public
        
        age 1살부터~ -11살
        
        -11 → 1살로 처리한다
        
       -![image](https://user-images.githubusercontent.com/70951555/141076210-2817ea57-48d0-4453-8767-73bb8d8bd3ae.png)

        
    
    - static : class
        
        슬라임 클래스
        
        파란 슬라임 주황슬라임 인스턴스
        
        만들때마다 static으로 클래스 내부에 선언 된 변수에 count++;
        
    
    - 상속
        
        `extends`
        
        - 오버로딩 : 같은 이름의 함수를 여러개 정의할 수 있는 것. 매개변수의 타입이 달라도 오버로딩을 할 수 있어요.
            
            ```jsx
            function print(a, b) {
            	console.log("a + b");
            }
            
            function print(a, b, c) {
            	console.log("a + b + c");
            }
            ```
            
        - 오버라이딩 : 상속관계에서 자식이 부모에게서 물려받은 함수를 재정의할 수 있는 것
            
            print() ⇒ console.log("하하 내가 부모다");
            
            print() ⇒ console.log("난 자식이지롱");
            
            → 자바스크립트에서는 오버로딩이 없다고 합니다...
            
            ![image](https://user-images.githubusercontent.com/70951555/141076242-c1e10b97-8016-4b14-8d10-6ab07ed76b04.png)

            
            `&operator=` 연산자 =을 오버로딩한 것
            
            ClapTrap의 인스턴스 ct1 ct2
            
            ct1 = ct2
            
            ```jsx
            ClapTrap &ClapTrap::operator=(const ClapTrap &org)
            {
            	if (this != &org)
            	{
            		this->hitPoints = org.hitPoints;
            		this->maxHitPoints = org.maxHitPoints;
            		this->energyPoints = org.energyPoints;
            		this->maxEnergyPoints = org.maxEnergyPoints;
            		this->level = org.level;
            		this->name = org.name;
            		this->meleeAttackDamage = org.meleeAttackDamage;
            		this->rangedAttackDamage = org.rangedAttackDamage;
            		this->armorDamageReduction = org.armorDamageReduction;
            	}
            	return *this;
            }
            ```
            
    
    - encapsulation : 캡슐화
        
        캡슐에 싸면 안보이겠죠? 은닉화
        
        내부 동작 원리를 다 알필요 없이 사용자가 편하게 사용할 수 있다.
        
        외부에서 접근해서 내부를 다 뜯어볼 수 없다.
        
    - polymorphism : 다형성
        
        슬라임 → 여러개를 찍어낼 수 있다.
        
        - 오버로딩, **오버라이딩***
        - 슬라임 상속 받은 슬라슬라임 클래스
    
- 김나윤
    
    [자바스크립트 코딩의 기술](https://www.notion.so/b51876f7f02640eaa9a8cd65e3f03ef7) 
    
- 양혜진
    
    [JavaScript Fetch API Tutorial with JS Fetch Post and Header Examples](https://www.freecodecamp.org/news/javascript-fetch-api-tutorial-with-js-fetch-post-and-header-examples/)
    
    - AJAX
    - axios
        
        호환성 이슈에 강함
        
    - fetch API
        
        ES6
        
        빠름
        
    
    데이터 형식
    
    - XML
    - JSON
    
    - serialize : obj → json
    - deserialize : json → obj
