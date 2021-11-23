## map() 적용시 key props를 부여하는 이유
<br>

React에서 map메소드를 통해 배열에 담긴 값을 컴포넌트에 넘겨주면서 여러번 렌더링 할 수 있다.

```jsx
{comments.map(el => {
	return <Comment comments={el} />;
})}
```


><img src="https://images.velog.io/images/pumpkin/post/458f7061-f7d2-494f-a721-7e1768433b5c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-11-23%2010.33.12.png" width="600px">
>
>- 하지만 map함수 사용시 key 값을 넘겨주지 않으면 이러한 에러가 발생한다. 각 리스트에는 고유의 키를 가져야 한다는 것이다.

<br><hr><br>

## Key
- Key는 React가 어떤 항목을 변경, 추가 또는 삭제할지 식별하는 것을 돕는다. key는 엘리먼트에 안정적인 고유성을 부여하기 위해 배열 내부의 엘리먼트에 지정해야 한다.

- Key를 선택하는 가장 좋은 방법은 리스트의 다른 항목들 사이에서 해당 항목을 고유하게 식별할 수 있는 문자열을 사용하는 것이다. 대부분의 경우 데이터의 ID를 key로 사용한다.


- 렌더링 한 항목에 대한 안정적인 ID가 없다면 최후의 수단으로 항목의 인덱스를 key로 사용할 수 있다.

```jsx
{comments.map((el, index) => {
	return <Comment key={index} comments={el} />;
})}
```

- 항목의 순서가 바뀔 수 있는 경우 key에 인덱스를 사용하는 것은 권장하지 않는다. 이로 인해 성능이 저하되거나 컴포넌트의 state와 관련된 문제가 발생할 수 있다.
