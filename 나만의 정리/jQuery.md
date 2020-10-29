# jQuery

### 💻 jQuery Tutorial
#### jQuery Syntax

- Basic syntax is: $(selector).action()

```javascript
$('button').click(function(){
	$('p').hide();
})
```

- A $ sign to define/access(정의/접근) jQuery
- A (selector) to "query (or find)" HTML elements
- A jQuery action() to be performed on the element(s)

```
Examples:
$(this).hide() - hides the current element.
$("p").hide() - hides all <p> elements.
$(".test").hide() - hides all elements with class="test".
$("#test").hide() - hides the element with id="test"
```

  - 문서 로드가 다 완료되기 전에 제이쿼리가 실행되는것을 막는 방법
 
```javascript
$(document).ready(function(){
	// jQuery methods go here...
});
// 위 아래 둘다 똑같이 작동한다.
$(function(){  
  // jQuery methods go here..._  
});
```

####  jQuery  Selectors
- $("") -> "" 안에 선택할 태그를 넣는다.
- id ->  $("#") / class -> $(".")
- 같은 이름을 가지고 있다면, 전체 다 고르는 것 같다 ex  document.querySelectorAll 처럼.. ?!
- [더 많은 선택자](https://www.w3schools.com/jquery/jquery_selectors.asp)
> 선택자가 굉장히 다양..! 참고해서 사용하면 좋을 것 같다.

#### jQuery  Event Methods
- css 로 주는 이벤트까지 다양하다
- [다양한 이벤트](https://www.w3schools.com/jquery/jquery_events.asp)

###  💻 jQuery Effects
####  jQuery Effects -  Hide and Show
- Hide, Show, Toggle, Slide, Fade, and Animate

```javascript
$(function(){
	$("#hide").click(function  () {
		$("p").hide(1000);
	})
	$("#show").click(function  () {
		$("p").show()
	})
})
```

- hide(여기에 숫자를 입력하면 speed 를 줄 수있다.)
- toggle 에도 마찬가지 ! 
- 숫자 뿐만 아니라 "slow"같은 string 값도 가능!

> js 초반에 toggle도 너무 어려웠는데 제이쿼리는 정말 확실히 간편하다..!

####  jQuery Effects -  Fading

```
Examples
jQuery fadeIn()
Demonstrates the jQuery fadeIn() method.

jQuery fadeOut()
Demonstrates the jQuery fadeOut() method.

jQuery fadeToggle()
Demonstrates the jQuery fadeToggle() method.

jQuery fadeTo()
Demonstrates the jQuery fadeTo() method
 ```

- fadeIn & fadeOut 속성에도 "slow, fast, number" 사용 가능

```javascript
$("button").click(function  () {
	$("#box1").fadeTo("slow",  0.15);
	$("#box2").fadeTo("slow",  0.45);
	$("#box3").fadeTo("slow",  0.65);
})
```

- slow 로 속도 조정 
- 0.15 -> opacity 조정 가능

#### jQuery Effects -  Sliding
- slideDown() /  slideUp() / slideToggle()
- 스피드를 콜백인자로 줄 수 있다.

#### jQuery Effects -  Animation
- $(_selector_).animate({_params_}_,speed,callback_);
- _params_-> css 필수값 
- speed는 옵션값 ( ex slow fast milliseconds )
- css 여러값을 보내줄 수 있고, += -= 가능, 'show', 'hidden', 'toggle'도 가능

#### jQuery  Stop Animations
- The jQuery stop() method is used to stop animations or effects before it is finished.
- $(_selector_).stop(_stopAll,goToEnd_);

#### jQuery  Callback  Functions
- js 는 한줄씩 코드를 읽어나가는데, 하나의 행동이 다 끝나지 않음에도 다음줄을 진행해서 에러가 난다. -> 이것을 막기위해 콜백함수 이용
- **$(_selector_).hide(_speed,callback_);**

```javascript
$("button").click(function(){  
	$("p").hide("slow", function(){  
		alert("The paragraph is now hidden");  
	});  
});
```

- The example below has a callback parameter that is a function that will be executed(처형,사형되다) after the hide effect is completed.

#### jQuery -  Chaining
- With jQuery, you can chain together actions/methods.
- Chaining allows us to run multiple jQuery methods (on the same element) within a single statement.

```javascript
$("#p1").css("color", "red").slideUp(2000).slideDown(2000);
```

- jQuery는 엄격한 구문이 아니기때문에 들여쓰기, 줄바꿈에 자유롭다

###  💻 jQuery HTML
#### jQuery -  Get Content and Attributes
- Get Content - text(), html(), and val()
- text() : Sets or returns the text content of selected elements
- html() : Sets or returns the content of selected elements (including HTML markup)
- val() : Sets or returns the value of form fields
- The jQuery `attr()` method is used to get attribute values.

#### jQuery -  Set Content and Attributes
- Set Content - text(), html(), and val()
-   text()  : Sets or returns the text content of selected elements
-   html()  : Sets or returns the content of selected elements (including HTML markup)
-   val()  : Sets or returns the value of form fields
- `text()`,  `html()`, and  `val()`, also come with a callback function. The callback function has two parameters: the index of the current element in the list of elements selected and the original (old) value. You then return the string you wish to use as the new value from the function.

- The following example demonstrates  `text()`  and  `html()`  with a callback function:
- attr 도 값을 set할 수 있고, multiple하게도 가능, 콜백함수로도 사용 가능

#### jQuery -  Add Elements
-   `append()`  - Inserts content at the end of the selected elements
-   `prepend()`  - Inserts content at the beginning of the selected elements
-   `after()`  - Inserts content after the selected elements
-   `before()`  - Inserts content before the selected elements
- The jQuery  `after()`  method inserts content AFTER the selected HTML elements.
- The jQuery  `before()`  method inserts content BEFORE the selected HTML elements.
- append, prepend, after, before 모두 여러개의 새 요소를 추가할 수 있다.

<img src="Add Several New Elements With append() and prepend()">

> 아직 정확하게 이해가 되지 않아서, 예시와 설명 첨부

#### jQuery -  Remove Elements
- 여기서부터!

