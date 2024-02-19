# 01. Styled Components - 소개, 사용  

## 1. CSS-in-Js란?  
> 자바스크립트 코드로 CSS 코드를 작성하여 컴포넌트를 꾸미는 방식  

#### 사용하면 좋은점  
컴포넌트를 만들고 컴포넌트를 꾸미기 위해 css 파일을 만들어서 import 하고 HTML tag 마다 classname를 넣고 CSS 코드를 작성하는 것을 반복하는 것을 줄일 수 있다.  

## 2. styled-components  
- styled-components는 리액트에서 CSS-in-JS 방식으로 컴포넌트를 꾸밀수 있게 도와주는 패키지  

```  
패키지란, React에는 없는 기능이지만 우리가 추가로 가져와서 사용할 수 있는 써드파티 프로그램
패키지들은 누군가에 의해 만들어진 것으로 npm에 모여있다.
사용하고자 하는 패키지를 npm install 또는 yarn add 를 통해서 설치
```  


#### styled-components 준비
-  styled-components 플러그인 설치   
![alt text](image.png)

- yarn add styled-components  


#### styled-components 사용하기  
```js
// src/App.js

import React from "react";
// styled-components에서 styled 라는 키워드를 import 합니다.
import styled from "styled-components";

// styled키워드를 사용해서 styled-components 방식대로 컴포넌트를 만듭니다. 
const StBox = styled.div`
	// 그리고 이 안에 스타일 코드를 작성합니다. 스타일 코드는 우리가 알고 있는 css와 동일합니다.
  width: 100px;
  height: 100px;
  border: 1px solid red;
  margin: 20px;
`;

const App = () => {
	// 그리고 우리가 만든 styled-components를 JSX에서 html 태그를 사용하듯이 사용합니다.
  return <StBox>박스</StBox>;
};

export default App;
```  

![alt text](image-1.png)

> 핵심이 되는 코드는 const StBox = styled.div``; 이 부분 이 방식대로 styled-components를 만드는 것  


#### 조건부 스타일링 구현   
```js
// src/App.js

import React from "react";
import styled from "styled-components";

// 1. styled-components를 만들었습니다.
const StBox = styled.div`
  width: 100px;
  height: 100px;
  border: 1px solid ${(props) => props.borderColor}; // 4.부모 컴포넌트에서 보낸 props를 받아 사용합니다. 
  margin: 20px;
`;

const App = () => {
  return (
    <div>
			{/* 2. 그리고 위에서 만든 styled-components를 사용했습니다. */}
			{/* 3. 그리고 props를 통해 borderColor라는 값을 전달했습니다. */}
      <StBox borderColor="red">빨간 박스</StBox>
      <StBox borderColor="green">초록 박스</StBox>
      <StBox borderColor="blue">파랑 박스</StBox>
    </div>
  );
};

export default App;
```    
![alt text](image-2.png)  




<hr>

<br>
<br>


# 02. Styled Components - GlobalStyles, Sass 소개, css reset
> tyled components는 컴포넌트 내에서만 활용가능하며 공통적으로 들어가야 할 스타일을 적용해야 할 경우 전역적으로(globally)’ 스타일을 지정한다. 라고 표현 그럴 때 적용하는 방법이 바로 전역 스타일링

## 1 GlobalStyles 적용  
> GlobalStyle.jsx  
```js
import { createGlobalStyle } from "styled-components";

const GlobalStyle = createGlobalStyle`
  body {
    font-family: "Helvetica", "Arial", sans-serif;
    line-height: 1.5;
  }
`;

export default GlobalStyle;
```  

> App.jsx
```js
import GlobalStyle from "./GlobalStyle";
import BlogPost from "./BlogPost";

function App() {
	const title = '전역 스타일링 제목입니다.';
	const contents = '전역 스타일링 내용입니다.';
  return (
    <>
      <GlobalStyle />
      <BlogPost title={title} contents={contents} />
    </>
  );
}

export default App;
```

## 2 css reset  
```css
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
```  

```js
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="./reset.css" />
  </head>
  <body>
    <span>Default Style을 테스트 해 봅니다.</span>
    <h1>이건 h1 태그에요</h1>
    <p>이건 p 태그에요</p>
  </body>
</html>
```  
![alt text](image-3.png)





<hr>

<br>
<br>


# 03. React Hooks

## 1 useState

> 선언  

```js
const [state, setState] = useState(initialState);
```  

> 업데이트   
```js
// 기존에 사용하던 방식
setState(number + 1);

// 함수형 업데이트 
setState(() => {});
```  

🛑 두 방식의 차이점
- 일반 업데이트 방식으로 onClick안에서 setNumber(number + 1) 를 3번 호출해도 number가 1씩 증가한다.
```js
import { useState } from "react";

const App = () => {
  const [number, setNumber] = useState(0);
  return (
    <div>
			{/* 버튼을 누르면 1씩 플러스된다. */}
      <div>{number}</div> 
      <button
        onClick={() => {
          setNumber(number + 1); // 첫번째 줄 
          setNumber(number + 1); // 두번쨰 줄
          setNumber(number + 1); // 세번째 줄
        }}
      >
        버튼
      </button>
    </div>
  );
}

export default App;
```

- 함수형 업데이트 방식으로 동일하게 작동하면 number가 3씩 증가
```js
// src/App.js

import { useState } from "react";

const App = () => {
  const [number, setNumber] = useState(0);
  return (
    <div>
			{/* 버튼을 누르면 3씩 플러스 된다. */}
      <div>{number}</div>
      <button
        onClick={() => {
          setNumber((previousState) => previousState + 1);
          setNumber((previousState) => previousState + 1);
          setNumber((previousState) => previousState + 1);
        }}
      >
        버튼
      </button>
    </div>
  );
}

export default App;
```


🛑 왜  다르게 동작하나?
**일반 업데이트 방식**은 버튼을 클릭했을 때 첫번째 줄 ~ 세번째 줄의 있는 setNumber가 각각 실행되는 것이 아니라, 배치(batch)로 처리한다. **즉 onClick을 했을 때 setNumber 라는 명령을 세번 내리지만, 리액트는 그 명령을 하나로 모아 최종적으로 한번만 실행**을 시킨다. 그래서 setNumber을 3번 명령하던, 100번 명령하던 1번만 실행됨    

<br>   

반면에 **함수형 업데이트 방식**은 **3번을 동시에 명령을 내리면, 그 명령을 모아 순차적으로 각각 1번씩 실행**시킨다.  0에 1더하고, 그 다음 1에 1을 더하고, 2에 1을 더해서 3이라는 결과값을 준다.  

<br>   
<br>   


🛑  왜 리액트팀은 useState가 위 방식으로 동작하도록 만들었을까?
> 공식문서에는 불필요한 리-렌더링을 방지(렌더링 최적화)하기 위해 즉, 리액트의 성능을 위해 한꺼번에 state를 업데이트 한다.


<br>
<br>


## 2 useState
> useEffect는 리액트 컴포넌트가 렌더링될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook 이다. 즉, 어떤 컴포넌트가 화면에 보여졌을 때 내가 무언가를 실행하고 싶다면? 또는 어떤 컴포넌트가 화면에서 사라졌을 때 무언가를 실행하고 싶다면? useEffect를 사용한다.

<br>

#### 사용 방법
```js
import React, { useEffect } from "react";
```  

```js
// src/App.js

import React, { useEffect } from "react";

const App = () => {

  useEffect(() => {
		// 이 부분이 실행된다.
    console.log("hello useEffect");
  });

  return <div>Home</div>;
}

export default App;
```  


- 활용
```js
import React, { useEffect, useState } from "react";

const App = () => {
  const [value, setValue] = useState("");

  useEffect(() => {
    console.log("hello useEffect");
  });

  return (
    <div>
      <input
        type="text"
        value={value}
        onChange={(event) => {
          setValue(event.target.value);
        }}
      />
    </div>
  );
}

export default App;
```

<br>

#### 의존성 배열
> 배열에 값을 넣으면 그 값이 바뀔 때만 useEffect를 실행하게 된다.

```js
// useEffect의 두번째 인자가 의존성 배열이 들어가는 곳 입니다.
useEffect(()=>{
	// 실행하고 싶은 함수
}, [의존성배열])
```

- 활용
```js
// src/App.js

import React, { useEffect, useState } from "react";

const App = () => {
  const [value, setValue] = useState("");
  useEffect(() => {
    console.log("hello useEffect");
  }, [value]); // value를 넣음

  return (
    <div>
      <input
        type="text"
        value={value}
        onChange={(event) => {
          setValue(event.target.value);
        }}
      />
    </div>
  );
}

export default App;
```

<br>

#### clean up
> 이제 컴포넌트가 사라졌을 때 무언가를 실행하는 것 이 과정을 우리는 클린 업 (clean up) 이라고 표현

```js
// src/App.js

import React, { useEffect } from "react";

const App = () => {

	useEffect(()=>{
		// 화면에 컴포넌트가 나타났을(mount) 때 실행하고자 하는 함수를 넣어주세요.

		return ()=>{
			// 화면에서 컴포넌트가 사라졌을(unmount) 때 실행하고자 하는 함수를 넣어주세요.
		}
	}, [])

	return <div>hello react!</div>
};

export default App;
```
<br>

#### 정리 
- `useEffect`는 화면에 컴포넌트가 mount 또는 unmount 됐을 때 실행하고자 하는 함수를 제어하게 해주는 훅이다.
- **의존성 배열을 통해 함수의 실행 조건을 제어**할 수 있다.
- `useEffect` 에서 함수를 1번만 실행시키고자 할때는 **의존성 배열을 빈 배열**로 둔다.


<hr>
<br>
<br>

## 3 useRef
> DOM 요소에 접근할 수 있도록 하는 React Hook 

- HTML과 javascript를 사용했을 때 특정 DOM을 선택하기 위해서 다음과 같이 했었다.
```js
// (1) getElementById 이용
const divTag = document.getElementById('#myDiv');

// (2) querySelector 이용
const divTag2 = document.querySelector('#myDiv');
```

#### 사용방법
```js
import "./App.css";
import { useRef } from "react";

function App() {
  const ref = useRef("초기값");
  console.log("ref", ref);

  return (
    <div>
      <p>useRef에 대한 이야기에요.</p>
    </div>
  );
}

export default App;
```  

🛑 콘솔을 확인해보면, ref에는 값이 이렇게 담겨있어요.  
> (중요) 이렇게 설정된 ref 값은 컴포넌트가 계속해서 렌더링 되어도 unmount 전까지 값을 유지  
![alt text](image-4.png)  

🛑 변경도 가능  
```js
import "./App.css";
import { useRef } from "react";

function App() {
  const ref = useRef("초기값");
  console.log("ref 1", ref);

  ref.current = "바꾼 값";
  console.log("ref 1", ref);

  return (
    <div>
      <p>useRef에 대한 이야기에요.</p>
    </div>
  );
}

export default App;
```  

#### state와 ref의 차이점
> state는 변경되면 렌더링이 되고, ref는 변경되면 렌더링이 안된다




#### DOM 접근

- 아이디, 패스워드 입력하는 ui 생성
```js
import "./App.css";

function App() {
  return (
    <>
      <div>
        아이디 : <input type="text" />
      </div>
      <div>
        비밀번호 : <input type="password" />
      </div>
    </>
  );
}

export default App;
```


- 아이디에 포커싱 주기
>     idRef.current.focus(); 사용
```
import { useEffect, useRef } from "react";
import "./App.css";

function App() {
  const idRef = useRef("");

  // 렌더링이 될 때
  useEffect(() => {
    idRef.current.focus();
  }, []);

  return (
    <>
      <div>
        아이디 : <input type="text" ref={idRef} />
      </div>
      <div>
        비밀번호 : <input type="password" />
      </div>
    </>
  );
}

export default App;
```





