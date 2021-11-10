- 김수연
    
    [Array](https://www.notion.so/code32/Array-c016b0f3f920440ca1390dc3c57d6121)
    

- 윤수진
    
    { destructuring, ...spread, ...rest }
    
    ### DESTRUCTURING
    
    구조 분해 할당. 비구조할당
    
    - Object Destructuring
        
        ```jsx
        const settings = {
        	color: {
        		theme: "dark"
        	}
        };
        
        console.log(settings.color);
        const { color } = settings;
        console.log(color);
        
        const { info : { follow = false }  = {} } = settings;
        console.log(follow);
        
        ```
        
    - renaming
        
        ```jsx
        const settings = {
        	color: {
        		chosen_color: "dark"
        	}
        };
        
        const { color: { chosen_color: chosenColor }} = settings;
        ```
        
        ```jsx
        let chosenColor = "blue";
        
        ({
        	color: { chosen_color: chosenColor = "light" }
        } = settings);
        ```
        
    - Array Destructing
        
        ```jsx
        const days = ["MON", "TUE", "WED", "THU", "FRI"];
        
        const [mon, tue] = days;
        
        console.log(mon, tue);
        ```
        
        ```jsx
        const days = () => ["MON", "TUE", "WED", "THU", "FRI"];
        
        const [mon, tue] = days();
        
        console.log(mon, tue);
        ```
        
    - Function Destructuring
        
        ```jsx
        function Container (props) {
        
        	props.name = ~~~
        	props.color = ~~~~
        }
        
        function Container ({ name, color }) {
        	name = ~~
        	color = ~~~
        }
        ```
        
    - swapping
        
        ```jsx
        let mon = "SAT";
        let sat = "MON";
        
        [sat, mon] = [mon, sat];
        ```
        
    - skipping
        
        ```jsx
        const days = ["mon", "tue", "wed", "thu", "fri"]
        
        const [, , , thu, fri] = days;
        console.log(thu, fri);
        ```
        
        → element가 너무 많다면 일단 인덱스를 쓰는걸로..!
        
    
    ### Spread
    
    - arr
        
        ```jsx
        const friends = [1, 2, 3, 4];
        const family = ["a", "b", "c"];
        
        console.log(friends);
        console.log(...friends);
        console.log(friends, family);
        console.log([...friends, ...family]);
        ```
        
    - obj → key가 겹치면 덮어씌워진다!!
        
        ```jsx
        const haha = {
        	name: 'bodhi',
        	age: 3,
        };
        
        const hello = {
        	merong: 'nala',
        	age: 4,
        };
        
        console.log({ ...haha, ...hello });
        ```
        
    - array 응용
        
        ```jsx
        const days = ["mon", "tue", "wed", "thu", "fri"]
        
        console.log([...days, "sat"]);
        console.log(["sun", ...days]);
        ```
        
    - obj 응용
        
        ```jsx
        const bodhi = {
        	username : "bodhi",
        };
        
        console.log({ ...bodhi, password:123 });
        ```
        
    
    ### Rest
    
    ```jsx
    const bestFriendMaker = (firstOne, ...rest) => {
    	console.log(`My dog is ${firstOne}`);
    	console.log(`My best friends are ${rest}`);
    };
    
    bestFriendMaker("보리", "나윤", "수연", "혜진");
    ```
    
    ```jsx
    const days = ["mon", "tue", "wed", "thu", "fri"]
    
    const [mon, tue, wed, ...rest] = days;
    
    const [mon, tue, wed] = days;
    ```
    

- 김나윤
    
    [비전공자를 위한 이해할 수 있는 IT 지식](https://gamy-curler-226.notion.site/IT-230be9381698465fb36a5fe555c7b50f)
    
    1-4장!
    

- 양혜진
    
    [JS 모듈화와 Webpack](https://www.notion.so/JS-Webpack-bf1179d2e82642189571c75c678450c4)
