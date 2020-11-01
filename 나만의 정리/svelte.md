# Svelte 튜토리얼

> *튜토리얼을 진행하면서 정리하고싶은 내용, 특별하다고 생각한 내용을 정리해 보고자 한다*.

## Introduction - 소개

- 스벨트 설치 방법

- 데이터를 추가 → script 에서 정의내려준 변수를 html 에서 {} 로 사용

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bfa7e769-bc72-4436-883c-18bfdc493d60/adding_data_.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bfa7e769-bc72-4436-883c-18bfdc493d60/adding_data_.png)

- 태그안의 옵션값을 지정해줄때도 동일하다

```jsx
<script>
let src = 'tutorial/image.gif';
</script>

<img {src} alt="tutorial">
```

- 이외에 스타일속성, 컴포넌트 import 는 다른 프레임 워크와 동일하다.
- **단, app.svelte에서 정의한 스타일은 import 해온 다른 컴포넌트에 적용되지 않는다.**

---

## Reactivity - 반응성

- 클릭 이벤트를 사용하고 싶을때 위의 옵션값 처럼 {}를 이용해서 사용한다.
- svlete 에만 있는 특별한 **$ 문법**
- **Svelte's reactivity is triggered by assignments, using array methods like push and splice won't automatically cause updates.**
- $ 문법의 비동기 처리로 인해 발견한 문제

---

## Props

- export 는 부모컴포넌트 -> 자식컴포넌트로 값을 전달받았다 라는 의미로 사용
- props 의 기본값을 설정해 주지 않으면 , undefined 라는 값이 출력 된다.

---

## Logic

- if 문을 이용할때는 → { #if 조건 } { /if } 또는 { #if 조건 } { :else } { /if } 또는 { #if 조건 } { :else if 조건 } { :else } { /if }
- for 문과 같은 반복문 → { #each 반복할배열 as 배열, i }{ /each }
- 비동기 처리 데이터를 위한 await

---

## Events

- on: 지시문을 이용하여 이벤트 수신
- 이벤트 수식어 / 수식어를 연결해서 사용할 수 있다. ( ex on:click|once={이벤트이름})
- 컴포넌트 이벤트 : createEventDispatcher를 이용해서 상위 컴포넌트에 전달
- DOM 이벤트 전달

---

## Bindings

- input 에 bind:value={} / bind:checked={}
- bind:group있는 경우 value속성 과 함께 사용

---

## Lifecycle

- **onMount** : DOM에 처음 렌더링 된 후에 실행되는 일
    - onMount 네트워크를 통해 데이터를 로드 하는 핸들러를 추가
- **onDestroy** : 컴포넌트가 화면에 제거되었을 때 실행되는 일
    - 메모리 누수를 방지할 수 있다.
    - 구성 요소를 초기화하는 동안 수명주기 함수를 호출하는 것이 중요하지만 어디에서 호출 하는지 는 중요하지 않습니다 . → 도우미 함수로 추상화 시킬 수 있다.
- **beforeUpdate** : DOM이 업데이트 되기 직전 호출
- **afterUpdate** : 화면에 값이 업데이트된 이후 호출
- **tick** : 언제든지 호출 할 수 있다는 점에서 다른 수명주기 함수와 다름
    - svelte 는 데이터의 변경을 즉각적으로 처리하지 않고 쌓아두었다가 한번에 바꾸게 됨으로써 불필요한 동작을 줄이고 브라우저가 효율적으로 작업할 수 있다. → tick 으로 이 문제를 해결
- 실제 라이프사이클 순서를 콘솔에 찍는다면?

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68d96cf1-61ae-4efb-9d74-956de187fac7/notion_.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68d96cf1-61ae-4efb-9d74-956de187fac7/notion_.png)

    - **beforeUpdate → onMount → afterUpdate**

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d676dfe2-ea15-4b3f-a92a-e0a497f6b3ba/notion_2.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d676dfe2-ea15-4b3f-a92a-e0a497f6b3ba/notion_2.png)

    - 상태값이 변경되면 **beforeUpdate → afterUpdate**
    - 컴포넌트가 제거 되면 onDestroy가 발생한다고 하는데, 아직 확인하지 못했다.
    - 다른 블로그들을 참고하면 **beforeUpdate → onMount → afterUpdate → onDestroy** 라고 한다...!

---

## Stores

- **writable**로 생성된 변수는 set / update / subscribe 메소드를 가진다.
    - set 은 값 설정
    - update 는 값 변경
    - subscribe는 관찰하고 있는 값이 변경될때마다 subscribe 함수의 콜백함수 실행

    > 튜토리얼 글로만은 이해가 잘 안되서 블로그 참고

    [[Svelte] Store](https://beomy.github.io/tech/svelte/store/)

    - 그렇다면 writable(0) / writable([]) → 정확한 의미는 무엇일까?
        - const count = writable(0); → count = 0;
        - const list = writable([]); → list = [];
- 위에 writable로 값을 변경하는것이 보기에는 정상적이어 보이지만 버그를 불러일으킨다. 그렇기 때문에 onDestroy 를 이용해야한다.
- 위의 과정을 스벨트는 **자동구독**으로 대신해준다. → $
    - onDestroy 사용하지 않고 count의 값을 새 변수로 할당 해주지 않아도 $를 붙여서 사용하면 해결된다!
    - ex $count
- 모든 store 에 값을 변경할 수 있는건 아닌데, **Readable** 는 사용자가 값을 변경하지 못하고 읽어오기만 가능하다.

    ```jsx
    // store.js
    import { readable } from 'svelte/store';

    export const time = readable(null, function start(set) {
    	// implementation goes here
    	const interval = setInterval(()=> {
    		set(new Date())
    	}, 1000)

    	return function stop() {
    		clearInterval(interval)
    	};
    });
    ```

    - subscribe 메소드를 가지고 있다.
    - 첫번째 인자는 초기값 (  null 이나 undefined 사용 가능 )
    - 두번째 인자로 함수를 넘겨주고 set을 콜백 ( 관찰값을 변경 )하고 stop(구독을 중단하면 호출)을 리턴하는 함수

    > 참고한 사이트

    [[Svelte] Store](https://beomy.github.io/tech/svelte/store/#readable-%ED%95%A8%EC%88%98)