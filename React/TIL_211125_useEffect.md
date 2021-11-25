# useEffect

웹 사이트를 만들다 보면 화면에 보일 수 있는 데이터를 서버에서 받아오기도 하고, state가 바뀔 때마다 함수를 실행 시키거나 이벤트리스너를 달았다가 해제하는 등의 동작이 필요하다. 이럴때 `useEffect` hook이 필요로 한다.

`useEffect` hook을 이해하는데 중요한 것은 발생 시점이다. 컴포넌트가 화면에 올라가고 내려가고 업데이트 되는 과정 속에서, 어느 시점에 훅이 발생하는지 파악해야 한다.

## 1. Side Effect
부작용, 부수효과라고 부르지만 프로그래밍 측면에서의 Side Effect는 부정적인 의미로만 사용되지 않는다.
함수가 어떤 동작을 할때, input - output 이외의 다른 값을 조작하면, 이 함수에 `Side Effect`가 있다고 표현한다
> 컴퓨터 과학에서 함수가 결과값 이외에 다른 상태를 변경시킬 때 부작용이 있다고 말한다.


```jsx
EX)
let count = 0;

function hello(name) {           // Input
  conunt = count + 1;            // Side Effect!
  return `${name}님 안녕하세요`;    // Output
}
```
함수 중간에 외부에 있는 count변수를 조작하므로 SideEffect가 발생한것이다.
이러한 SideEffect는 리액트 함수 컴포넌트에서도 일어날 수 있다.
state와 props를 받아서 UI를 그려내는 것 이외의 행위를 SideEffect라고 할 수 있다.
대표적으로 Data Fetching, DOM에 직접 접근(ex. Event Listerner 등록), 구독(ex. setInterval)과 같은 행위 들이 있다.

<br>

## 2. useEffect

### 1. useEffect
앞서 말한 SideEffect들은 함수 안에 그냥 실행 시키면 안된다.
함수 컴포넌트 리턴 값은 UI요소 이고 state, props의 변화가 있을때마다 함수가 실행된다 이말은 렌더링 될 때마다 함수 안의 로직이 실행된다는 뜻이다.

```jsx
import { useEffect } from 'react';

function hello({name}) {                   // Input
  useEffect(() => {
    document.title = `${name}님 안녕하세요!`; // Side Effect
  }, [name]);
  
  return <div>{`${name}님 안녕하세요!`}</div>; // Output
}
```
그래서 리액트는 이런 SideEffect를 일으키기 적절한 장소로 `useEffect` 훅을 제공한다.
`useEffect`는 SideEffect를 렌더링 이후에 발생시킨다. `useEffect`가 수행된느 시점에 이미 DOM이 업데이트됨을 보장한다는 뜻이고, SideEffect가 렌더링에 영향을 주지 않도록 설계되었음을 의미한다.

<br>

### 2. Rendering Cycle with useEffect
```jsx
import { useEffect } from "react"

useEffect(실행시킬 동작, [타이밍])

useEffect(() => {
  //SideEffect
})              // 매 렌더링마다 SideEffect가 실행되어야 하는 경우

useEffect(() => {
  //SideEffect
}, [value])     // SideEffect가 첫번째 렌더링 이후 한번 실행되고, 이후 특정 값의 업데이트를 감지했을 때마다 실행되어야하는 경우

useEffect(() => {
  //SideEffect
}, [])          // SideEffect가 첫번째 렌더링 이후 한번 실행되고, 이후 어떤 값의 업데이트도 감지하지 않도록 해야 하는 경우
```

![](https://images.velog.io/images/pumpkin/post/adc37d5c-306f-493b-80d5-7c0717f292b9/image.png)
