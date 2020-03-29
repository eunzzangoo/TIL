# 📖 Week_01 미션

> 최초 작성일:  2020년 03월 25일



1. JavaScript - FE

   1) 자바스크립트 배열

    * forEach, map, filter

      * forEach

      ```js
      var fruits = ["apple", "orange", "cherry"];
      fruits.forEach(myFunction);
      
      function myFunction(item, index) {
        document.getElementById("demo").innerHTML += index + ":" + item + "<br>";
      }
      ```

      * map

      ```js
      var numbers = [65, 44, 12, 4];
      var newarray = numbers.map(myFunction) 
      
      function myFunction(num) {
        return num * 10; //새로운 배열 반환
      }
      
      document.getElementById("demo").innerHTML = newarray;
      ```

      * Fileter

      ```js
      var ages = [32, 33, 16, 40];
      
      function checkAdult(age) {
        return age >= 18; //true, false 반환
      }
      
      function myFunction() {
        document.getElementById("demo").innerHTML = ages.filter(checkAdult);
      }
      ```

> [참고: javascript Array](https://www.w3schools.com/jsref/jsref_obj_array.asp)



​	2) 자바스크립트 객체

 * 실습 해보기

   	* 실습 1: 주어진 데이터를 이용하여 숫자타입으로 구성된 요소를 뽑아 배열 만들기, [json data link](https://gist.github.com/crongro/ade2c3f74417fc202c8097214c965f27)

   ```javascript
   var result = [];
   //Object.key()를 사용하여 키가 담긴 배열 반환
   Object.keys(data).forEach(function(v){
       for(key in data[v]){
          if(typeof data[v][key]=="number"){
              result.push(key);
          }
      } 
   })
   
   console.log(result);
   ```

   * 실습 2: type이 sk인, name으로 구성된 배열 출력 해보기, [json data link](https://gist.github.com/crongro/a9a118977f82780441db664d6785efe3)

   ```javascript
   var result = [];
   
   function search(data) { 
       data.forEach(element => {
           if(element.type == "sk")
               result.push(element.name);
           if(element.childnode)
               search(element.childnode);
       });
   }
   search(data);
   console.log(result);
   ```



2. DOM API 활용 - FE

   1) DOM Node 조작하기

   * 탐색 (tagName, textContent, nodeType)

     * [tagName](https://www.w3schools.com/jsref/prop_element_tagname.asp) : 태그 이름 얻기

     * [textContent](https://www.w3schools.com/jsref/prop_node_textcontent.asp) : string  텍스트 내용 얻기
     * [nodeType](https://www.w3schools.com/jsref/prop_node_nodetype.asp) :  노드 고유의 타입 얻기

   * 이동 (childNodes, firstChild, firstElementChild, parentElement, nextSibling, nextElementSibling)

     * [childNodes](https://developer.mozilla.org/en-US/docs/Web/API/Node/childNodes), [firstChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/firstChild) : 자식 노드 탐색하기
     * firstElementChild : 첫번째 자식 노드
     * [parentElement](https://developer.mozilla.org/en-US/docs/Web/API/Node/parentElement) : 부모 요소 노드
     * [nextSibling](https://developer.mozilla.org/en-US/docs/Web/API/Node/nextSibling), [nextElementSibling](https://developer.mozilla.org/en-US/docs/Web/API/NonDocumentTypeChildNode/nextElementSibling): 다음 형제 노드에 대한 정보, 형제요소 노드

   * 조작 (removeChild, appendChild, insertBefore, cloneNode, replaceChild, closest)

     * [removeChild](https://developer.mozilla.org/ko/docs/Web/API/Node/removeChild) : 노드를 제거
     * [appendChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild) : 자식 노드의 마지막에 노드를 추가
     * [insertBefore](https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore) : 전달인자 2개, (삽입하려는 노드, 삽입기준의 노드), 인자가 1개라면 == appendChild
     * [cloneNode](https://developer.mozilla.org/ko/docs/Web/API/Node/cloneNode) : 노드복제하기

     * [replaceChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/replaceChild) : 기존 노드 교체
     * [closest](https://developer.mozilla.org/ko/docs/Web/API/Element/closest) : 자신으로부터 출발하여 가장 가까운 부모요소 반환, 조건없으면 null 반환

   * HTML을 문자열로 처리해주는 API (innerText, innerHTML, insertAdjacentHTML)

     * [innerText](https://developer.mozilla.org/ko/docs/Web/API/Node/innerText) : 보이는 텍스트 값만 가져옴
     * [innerHTML](https://developer.mozilla.org/ko/docs/Web/API/Element/innerHTML) : HTML 구조까지 모두 복사
     * [insertAdjacentHTML](https://developer.mozilla.org/ko/docs/Web/API/Element/insertAdjacentHTML) : 시작 태그 앞 뒤, 종료 태그 앞 뒤 노드삽입

    * 생각하기: DOM의 특정 영역을 insertAdjacentHTML 메서드를 사용해서 추가해보세요. [참조: document](https://developer.mozilla.org/ko/docs/Web/API/Element/insertAdjacentHTML)

       * `element.insertAdjacentHTML(position, text);` 
       * Position 예시 그림

      ```
      <!-- beforebegin -->
      <p>
      <!-- afterbegin -->
      foo
      <!-- beforeend -->
      </p>
      <!-- afterend -->
      ```

      * 예시

      ```javascript
      // <div id="one">one</div>
      var d1 = document.getElementById('one');
      d1.insertAdjacentHTML('afterend', '<div id="two">two</div>');
      
      // At this point, the new structure is:
      // <div id="one">one</div><div id="two">two</div>
      ```

      

   2) DOM API 실습

   * 실습1

   ```js
   /*
   strawberry 아래에 새로운 과일을 하나 더 추가하시오
   */
   var ul = document.querySelector("ul");
   var li = document.createElement("li");
   var mangoText = document.createTextNode("mango");
   
   li.appendChild(mangoText);
   ul.appendChild(li);
   ul.removeChild(ul.lastChild);
   ```

   * 실습2

   ```javascript
   /*
   insertBefore를 사용하여 orange와  banana 사이에 새로운 과일을 추가하시오
   */
   var ul = document.querySelector("ul");
   var li = document.createElement("li");
   var mangoText = document.createTextNode("mango");
   
   li.appendChild(mangoText);
   ul.insertBefore(li, ul.querySelector("ul li:nth-child(3)"));
   ```

   * 실습3

   ```javascript
   /*
   insertAdjacentHTML메서드를 사용해서 새로운 과일 추가
   */
   var ul = document.querySelector("ul");
   var banana = ul.querySelector("li:nth-child(3)");
   
   banana.insertAdjacentHTML("afterend",'<li> mango </li>');
   ```

   * 실습4

   ```js
   /*
   apple을 grape 와 strawberry 사이로 옮기시오.
   */
   var apple = document.querySelector("li:nth-child(1)");
   var strawberry = document.querySelector("li:nth-child(5)");
   
   var parent = document.querySelector("ul");
   
   parent.insertBefore(apple, strawberry);
   ```

   * 실습5

   ```js
   /*
   class 가 'red'인 노드만 삭제하시오.
   */
   var red = document.querySelectorAll(".red");
   
   red.forEach(function(element) {
   	element.remove();
   })
   ```

   * 실습6

   ```js
   /*
   section 태그의 자손 중에 blue라는 클래스를 가지고 있는 노드가 있다면, 그 하위에 있는 h2 노드를 삭제하시오.
   */
   var sec = document.querySelector("section");
   var blue = document.querySelectorAll(".blue");
   
   blue.forEach(function(element) {
     var section = element.closest("section");
     section.querySelector("h2").remove();
   })
   ```

   

> 참고: [w3schools](https://www.w3schools.com/jsref/prop_node_nodetype.asp)



3. Ajax - FE

1) Ajax 응답처리와 비동기

	*	동기작업은 작업이 완료될때까지 다음작업을 차단하지만 비동기 작업은 차단하지않고 실행할수있다.
	*	Ajax 응답처리 : 서버로 받아온 JSON 데이터를 자바스크립트 객체로 변환하기 위해 JSON  객체를 사용 [JSON.parse()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)

2) 디버깅 - 크롬 개발자 도구

* [크롬 개발자 도구](https://developers.google.com/web/tools/chrome-devtools?hl=ko)



4. Web Animation - FE

   1) 웹 애니메이션 이해와 setTimeout 활용

   ```javascript
   /* 
   setTimeOut(() => {
   	console.log('현재시각은', new Date());
   }, 500);
   */
   
   let count = 0;
   function animate(){
   	setTimeout(() => {
   		if(count >= 20) return;
   		console.log('현재시각은', new Date());
   		count++;
   		animate(); //재귀호출 
   	}, 500);
   }
   animate();
   ```

   

   2) requestAnimationframe 활용

   setTimeout을 개선한것이 requestAnimationframe!

   ```js
   var count = 0;
   var el=document.querySelector(".outside");
   el.style.left = "0px";
   
   function run() {
      if(count > 70) return; 
      count = count + 1;
      el.style.left =  parseInt(el.style.left) + count + "px"; //count값을 하나씩 증가시켜 1px씩 이동하는 애니메이션을 만들어볼수있음.
      requestAnimationFrame(run);
   }
   
   requestAnimationFrame(run);
   ```



​	3) CSS3 transition활용

 * Transitions을 이용하여 애니메이션을 구현할수있다. 이 방법은 Javascript로 구현하는것보다 더 빠르다. 

 * 더 빠른 css3 애니메이션 관련 속성들

   	*	Transform : translateXX();
   	*	transform : scale();
   	*	transform : rotate();
   	*	opacity

*	생각해보기

  *	특정 엘리먼트를 만들고, 그 엘리먼트에 transition 속성을 주고, hover했을 때 좌측 상단에서, 우측 하단으로 움직이는 animation을 만들어보세요.

  ```html
  <!DOCTYPE html>
  <html>
  <head>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
  .btn {
    background-color: #f4511e;
    border: none;
    color: white;
    padding: 16px 32px;
    text-align: center;
    font-size: 16px;
    margin: 4px 2px;
    opacity: 0.5;
    transition: all 100ms;
  }
  
  .btn:hover {opacity: 1}
  </style>
  </head>
  <body>
      <div>
          <button class="btn">Hover Over Me</button>
      </div>
  </body>
  
  <script>
      var div = document.querySelector("div");
      div.addEventListener("click",function(){
      div.style.transform="translate("+parseInt(window.innerWidth)+"px,"+parseInt(window.innerHeight)+"px)";
      });
      </script>
  </html>
  ```

  

  *	vendor prefix가 무엇이고, 왜 필요한지 알아봅니다.

    브라우저별로 따로 놀 수있는 css를 잡기위해 어떤 브라우저인지 알려주기 위한 접두사! 크롬과 사파리는 같은 웹킷 계열 브라우저 이므로 같은 벤더 프리픽스를 사용함.

  ```css
  <style>
  
      .button {
  
          background: red;          <!-- gradient 속성을 지원하지 않는 모든 브라우저를 위한 코드 -->
  
          background: -webkit-linear-gradient(red, yellow); <!-- 크롬과 사파리 4.0 이상을 위한 코드 -->
  
          background: -moz-linear-gradient(red, yellow);    <!-- 파이어폭스 3.6 이상을 위한 코드 -->
  
          background: -ms-linear-gradient(red, yellow);     <!-- 익스플로러 10.0 이상을 위한 코드 -->
  
          background: -o-linear-gradient(red, yellow);      <!-- 오페라 10.0 이상을 위한 코드 -->
  
          background: linear-gradient(red, yellow);         <!-- CSS 표준 문법 코드 -->
  
      }
  
  </style>
  ```



> 미션 인증샷~~~~😄
>
> ![스크린샷](https://github.com/eunzzangoo/TIL/blob/master/%EB%B6%80%EC%8A%A4%ED%8A%B8%EC%BD%94%EC%8A%A4_%EC%9B%B9%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EC%8B%A4%EC%A0%84/Week_01/스크린샷 2020-03-29 오후 9.04.22.png)

