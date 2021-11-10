- 수진
    
    복습
    
    - 실행 컨텍스트
        - 평가 -> 실행
        - 렉시컬 환경
            - 외부 환경 참조 OuterLexicalEnvironment Reference
            - 변수
            - 함수 등..
        - 링크드 리스트
    - 클래스
        - OOP
        - private, public
        - getter, setter
    
    새로운 개념!
    
    - 가비지 컬렉터 -> 더이상 참조하지 않으면 해제!
    - 클로저
        - 장단점
        - 활용
        
        전역실행컨텍스트 : closure -> f , haha -> closure()
        
        closure() 실행컨텍스트 // : >>> a -> undefined , inner -> f <<<
        
        haha() 실행컨텍스트 : -----
        
        ```
        function closure() {
        	let a = 1;
        	function inner() {
        		console.log(a);
        	}
        	return inner;
        }
        
        let haha = closure();
        haha();
        
        ```
        
        ```
        function useState(init) {
        	let state = init;
        
        	return [
        		function getState() {
        			return state;
        		}
        		function setState(newState) {
        			return state = newState;
        		}]
        	}
        
        const [num, setNum] = useState(0);
        [[Environment]]
        
        ```
        
        장점 : private인 것처럼 쓸 수 있다. -> 렉시컬 환경이 남아잇어서
        
        -> 외부 렉시컬 환경 참조를 통해 가비지 컬렉터가 아직 지우지 않은 렉시컬 환경이 남아있어서
        
        단점 : 메모리 누수가 날 수도??
        
- 혜진
    
    OSI 7layers와 firebase
    
- 수연
    
    HookState library
    
    [Hookstate - 상태 관리 라이브러리](https://www.notion.so/code32/Hookstate-ecbc87696e0d4c4db95a52e02d7874c4)
