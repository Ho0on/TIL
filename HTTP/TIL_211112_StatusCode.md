# Response Status Code
- 프로젝트를 진행하며 많이 보게 될 응답의 상태 코드이다

<br>

### 1. 200: OK
- 문제없이 요청에 대한 처리가 백엔드 서버에서 이루어지고 나서 오는 응답코드

<br>

### 201: Created
- 무언가가 잘 생성되었을 때에(Successfully Created) 오는 Status Code
- 대게 POST 메소드의 요청에 따라 백엔드 서버에 데이터가 잘 생성 또는 수정 되었을 때에 보내는 코드

<br>

### 400: Bad Request
- 해당 요청이 잘못되었을 때 보내는 Status Code
- 주로 요청의 Body에 보내는 내용이 잘못되었을 때 사용되는 코드 
ex) 전화번호를 보내야 하는데 숫자가 아닌 문자열의 주소가 대신 Body에 담겼을 경우

<br>

### 401: Unauthorized
- 유저가 해당 요청을 진행하려면 먼저 로그인을 하거나 회원가입이 필요하다는 의미 
ex) wish list, 좋아요 기능은 회원이 아니면 요청을 보낼 수 없음

<br>

### 403: Forbidden
- 유저가 해당 요청에 대한 권한이 없다는 뜻
- 접근 불가능한 정보에 접근했을 경우
ex) 오직 유료회원만 접근할 수 있는 데이터를 요청 했을 때

<br>

### 404: Not Found
- 요청된 URI 가 존재하지 않는다는 의미

<br>

### 500: Internal Server Error
- 서버에서 에러가 났을 때의 Status Code
- API 개발을 하는 백엔드 개발자들이 싫어하는 코드
