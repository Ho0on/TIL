# React Router

## 1. SPA
- `SPA ( Single Page Application )`: 서버로부터 완전한 새로운 페이지를 불러오지 않고 현재의 페이지를 동적으로 다시 작성함으로써 사용자와 소통하는 웹 애플리케이션이나 웹사이트
- 리액트 프로젝트에서 `라우팅`을 통해 동적으로 여러개의 페이지를 보여준다.

## 2. React Router
- `라우팅(Routing)`이란 다른경로(url 주소)에 따라 다른 View를 보여주는 것이다.
- `React-router`라는 리액트 라이브러리를 설치하여 라우팅 기능을 사용가능하다.

### 1) react-router 설치
```
npm install react-router-dom --save
```

### 2) Router 컴포넌트 구현
```jsx
import React from "react";
import {BrowserRouter, Routes, Route} from "react-router-dom";

import Page1 from "./pages/Page1";
import Page1 from "./pages/Page2";

function Router(){
  <BrowserRoute>
    <Routes>
      <Route path="/" element={<Page1 />} />
      <Route path="/page2" element={<Page2 />} />
    </Routes>
  </BrowserRoute>
}

export default Router;
```

> index.js 파일에서 아래와 같이 변경해야 라우팅 기능을 적용한 페이지를 보여준다.
>```jsx
>ReactDOM.render(<Router/>, document.getElementById('root'));
>```

### 3) Route 페이지 이동
**`<Link>`컴포넌트 사용**

```jsx
import React from "react";
import { Link } from "react-router-dom";

function Page1() {
  return (
    <div>
      <Link to="/page2">Page2로 이동</Link>
    </div>
  );
}

export default Page1;
```
- `<Link/>`컴포넌트는 DOM에서 `<a>`로 변환 된다.
    - `<Link/>` : 프로젝트 내에서 페이지를 전환하는 경우
    - `<a>` : 외부 사이트로 이동하는 경우 사용
    
    <br>

**`useNavigate`사용**

```jsx
import React from "react";
import { useNavigate } from "react-router-dom";

function Page1() {
  const navigate = useNavigate();

  const goToPage2 = () => {
    navigate("/page2");
  };

  return (
    <div>
      <button className="page2Btn" onClick={goToPage2}>
        Page2 이동
      </button>
    </div>
  );
}

export default Page1;
```

- 함수 호출을 통해 페이지를 이동
- `useNavigate` 훅을 실행하면 페이지 이동 함수를 반환한다.
- 변수 `navigate`에 함수를 담아 인자로 `Router.js`에서 설정한 경로를 넘겨주면, 해당 경로로 이동한다.

<br>

### 두 가지 차이점

**`<Link />`**
- 클릭 시 바로 이동하는 로직 구현 시에 사용
- ex) Nav Bar, 아이템 리스트 페이지에서 아이템 클릭 시 상세 페이지로 이동
<br>

**`useNavigate`**
- 페이지 전환 시 추가로 처리해야 하는 로직이 있는 경우 `useNavigate` 훅을 활용하여 구현
- ex) 로그인 버튼 클릭 시
    - Backend API로 데이터(User Info) 전송
    - User Data 인증 / 인가
    - response message
    - Case 1 : 회원 가입되어 있는 사용자 > Main 페이지로 이동
    - Case 2 : 회원 가입이 되어 있지 않은 사용자 > Signup 페이지로 이동
