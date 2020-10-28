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