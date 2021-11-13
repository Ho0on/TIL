# 1. HTTP

✅ _HyperText Transfer Protocol_

컴퓨터들끼리 HTML파일을 주고받을 수 있도록 하는 소통 방식 또는 약속이다.
<br/><hr><br/>

# 2. HTTP의 특징
### 1. Request / Response (요청/응답)

HTTP 통신의 핵심은 `요청`과 `응답`이다. transfer을 할때 보내는 주체가 받는 주체에게 요청을 보내고, 받는 주체는 요청을 보낸 주체에게 응답을 보낸다.

>예를 들어, 유튜브 영상을 볼때 링크를 클릭하면 내 컴퓨터는 구글의 서버에게 요청을 보낸다. 구글의 서버는 이요청을 처리해서 다시 요청을 보낸 내 컴퓨터에 응답을 보낸다.
HTTP를 어렵게 생각할 필요 없이 우리에게 친숙한 소통방식을 컴퓨터에 적용시킨 것이다.

<br/>

### 2. Stateless

State(상태) + less(없음)

각각의 HTTP통신은 `독립적`이기 때문에 과거의 통신에 대한 내용을 알지 못한다. 이전의 상태를 전혀 알지 못하기 때문에 매 통신마다 필요한 모든 정보를 담아서 요청을 보내야 한다.
    
>따라서, 만일 여러번의 통신의 진행과정에서 연속된 데이터 처리가 필요한 경우(ex. 쇼핑몰에서 로그인후 장바구니 기능)를 위해 로그인 토큰 또는 브라우저의 쿠키, 세션, 로컬스토리지 같은 기술이 만들어졌다.

<br/><hr><br/>
    
# 3. Request / Response
✅ 프론트엔드에서 백엔드에게 데이터를 요청하고 백엔드는 요청을 처리해서 응답을 준다. 요청과 응답에 대한 구조와 메세지를 잘 파악하면 에러를 잡을 수 있다.
    
## 1. Request 메세지 구조
    
`Start Line`: 요청의 첫번째 줄, 시작 줄도 세부분으로 구성
```
1. HTTP Method: 해당 요청이 의도한 액션을 정의. 주로 GET, POST, DELETE가 많이 쓰임
2. Request target: 해당 요청이 전송되는 목표 url
3. HTTP Version: HTTP의 버전을 뜻한다. 주로 1.1 버전

GET /login HTTP/1.1 
: GET 메소드로 login이라는 요청 타겟에 HTTP 1.1버전으로 요청을 보낸다.
```



`Headers`: 해당 요청에 대한 추가 정보(메타 데이터)를 담고있는 부분.
```
Headers: {
	Host: 요청을 보내는 타겟의 주소 (ex. www.apple.co.kr)
	User-Agent: 요청을 보내는 클라이언트의 정보 (ex. chrome, safari)
	Content-Type: 해당 요청이 보내는 메세지 body의 타입 (ex. application/json)
	Content-Length: body 내용의 길이
	Authorization: 회원의 인증/인가를 처리하기 위해 로그인 토큰을 담는다
}
```
`Body`: 해당 요청의 실제 내용. 주로 Body를 사용하는 메소드는 POST다.   
```
    ex) 로그인시 서버에 보낼 요청의 내용
    Body: {
    	"user_email": "aaa@gmail.com"
    	"user_password": "bbb"
    }
```
      
      
  <hr><br>
  
      
      

## 2. Response 메시지 구조
    
`Status Line`: 응답의 상태 줄. 응답은 요청에 대한 처리상태를 클라이언트에게 알려주면서 내용을 시작한다.
```
1. HTTP Version: 요청의 HTTP버전과 동일
2. Status Code: 응답 메세지의 상태 코드
3. Status Text: 응답 메세지의 상태를 설명해주는 텍스트

HTTP/1.1 404 Not Found
: 1.1버전으로 응답, 요청에 대해 정보를 찾을수 없기 때문에 404 메세지를 보낸다.
HTTP/1.1 200 SUCCESS
: 1.1버전으로 응답, 요청에 대해 성공하여 200 상태 메세지를 보낸다.
```

`Headers`: 요청의 헤더와 동일하다. 응답에서만 사용되는 헤더의 정보들이 있다. 예를 들어 요청하는 브라우저의 정보가 담긴 `User-Agent` 대신, `Server` 헤더가 사용된다.
   
`Body`: 응답도 응답의 형태에 따라 데이터를 전송할 필요가 없는 경우 Body가 없을 수도 있다. 주로 `JSON` 데이터 타입을 사용한다.
```
ex) 로그인 요청에 대해 성공했을때 응답의 내용
Body: {
	"message": "SUCCESS"
	"token": "dojwfxwefjo@jfowifj098"
}
```
