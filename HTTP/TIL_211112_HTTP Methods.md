# HTTP Methods

## HTTP Request Methods

### 1. GET
- 어떤 데이터를 서버로부터 받아올 때 주로 사용하는 메소드
- 데이터를 받아오기만 할 때 사용된다.
- 가장 간단하고 많이 사용되는 HTTP 메소드 (웹페이지를 띄울 때 필요한 정보들을 모두 GET으로 요청하여 받아온 것이다.)

>장바구니에 담은 제품을 조회
>```
>(축약된 요청 메세지)
>GET/shop/bag HTTP/1.1
>Headers: {
>   "HOST": "https://www.apple.com/kr"
>   "Authorization": "sdfjowjefoi@oiwefj34on" (유저가 본인임을 증명하는 인증/인가 토큰)
>}
>
>(축약된 응답 메시지)
>HTTP/1.1 200 SUCCESS
>Body: {
>   "message": "SUCCESS"
>   "carts": [
>   {
>     "productId": 10
>     "name": "Pro Display XDR"
>     "price": "₩7,899,000"
>     "quantitiy": 1
>   },
>   {
>     "productId": 20
>     "name": "Mac Pro"
>     "price": "₩73,376,000"
>     "quantity": 2
>   }
>  ]
> }
>```
<br/><hr><br/>

### 2. POST
- 데이터를 생성 / 수정 할 떄 주로 사용되는 메소드
- 데이터를 생성 및 수정 할 때 많이 사용되기 떄문에 대부분의 경우 요청에 body가 포함돼서 보내진다.

>장바구니에 상품을 담는다.
>```
>(축약된 요청 메세지)
>POST /shop/bag HTTP/1.1
>Headers: {
>   "HOST": "https://www.apple.com/kr"
>   "Authorization": "sdfjowjefoi@oiwefj34on" (유저가 본인임을 증명하는 인증/인가 토큰)
>}
>Body: {
>   product: {
>       "productId": 30
>       "name": "12.9형 iPad Pro Wi-Fi + Cellular 128GB"
>       "price": "₩1,499,000"
>       "color": "스페이스 그레이"
>       "quantity": 1
>   }
>}
>
>(축약된 응답 메시지)
>HTTP/1.1 201 SUCCESS
>Body: {
>   "message": "SUCCESSFULLY CARTS UPDATED"
>}
>```
<br/><hr><br/>

### 3. DELETE
- 특정 데이터를 서버에서 삭제 요청을 보낼때 쓰는 메소드

>장바구니에서 상품을 삭제한다.
>```
>(축약된 요청 메세지)
>DELETE /shop/bag/30 HTTP/1.1
>Headers: {
>   "HOST": "https://www.apple.com/kr"
>   "Authorization": "sdfjowjefoi@oiwefj34on" (유저가 본인임을 증명하는 인증/인가 토큰)
>}
>
>(축약된 응답 메시지)
>HTTP/1.1 201 SUCCESS
>Body: {
>   "message": "productId 30 DELETED"
>}
>```
<br/><hr><br/>
