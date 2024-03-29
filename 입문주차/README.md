# 1-4 개발환경 셋팅

### 1. 크롬 설치
- [크롬 다운로드](https://www.google.com/intl/ko_kr/chrome/)

### 2. 비주얼 스튜디오 설치
- [비주얼 스튜디오 다운로드](https://visualstudio.microsoft.com/ko/downloads/)

### 3. git 설치
- [git 다운로드](https://git-scm.com/downloads)

### 4. node.js 설치
- [node.js 다운로드](https://nodejs.org/ko/)
  
 > node 설치 확인하기
  ```
  node -v
  ```
![image](https://github.com/whitewise95/-/assets/81284265/a9040a62-42cb-4b91-a7ab-fbf6865ef667)


### 5. yarn 설치
- 터미널에서 yarn 설치  
  ```bash
  npm install -g yarn
  ```
  
- yarn 설치 확인  
  ```
  yarn -v 
  ```

### 6. npm과 yarn에 대해  
 **공통적 특징** 
 1. 둘다 자바스크립트 **런타임 환경** 인 노트(Node.js)의 패키지 관리자  
 2. 애플의 앱스토어, 구글의 플레이스토어처럼, 전 세계의 많은 개발자들이 본인들이 만든 유용하고 다양한 패키지들 또는 프로그램을 ‘온라인 데이터베이스’에 올려놓는다. 그걸 쉽게 설치하고 삭제할 수 있도록 도와주는 관리자
  
    
#### **차별적 특징**
- NPM
    1. node.js를 설치할 때 자동으로 생성
    2. Node Package Manager의 약자
    3. NPM platform 자체
- YARN
    1. 2016년에 페이스북에서 개발한 패키지 관리자
    2. npm과의 호환성이 좋고, 속도나 안정성 측면에서 npm보다 월등히 좋다.
- 요약
    1. 속도 : Yarn wins
    2. 보안 : Yarn wins(하지만 최근 npm의 보안 업데이트도 크게 향상)
 

- 명령어  
![image](https://github.com/whitewise95/-/assets/81284265/6f331554-e4bd-46b8-81fb-cccca8f2605f)





<hr>

<br>
<br>





# 1-5 CRA(Create React App)
```
[학습 목표]

1. CRA의 개념에 대해 설명할 수 있습니다.
2. CRA 명령어로 프로젝트를 생성하고 열 수 있습니다.
3. 왜 CRA로 생성한 웹 애플리케이션이 열리게 되는지 대략적인 흐름을 설명할 수 있습니다.
4. 상대경로와 절대경로의 개념에 대해 숙지하고, 리액트 프로젝트 내에서 절대경로를 사용하는 방법을 알 수 있습니다.
```


## 1 CRA란 무엇일까요?
한 줄의 명령어 입력으로 React 프로젝트 개발에 필수요소를 자동으로 구성하는 방법, React 프로젝트를 구성하기 위해 필요한 것들은 상당히 많은데 이러한 것들을 신경쓰지 않아도 알아서 만들어준다.


## 2 CRA로 프로젝트 생성하기
```
ls #현재 내가 위치하고 있는 곳이 어디인지 확인

cd 폴더이름 #리액트 프로젝트를 생성하고 싶은 폴더로 접근

yarn create react-app week-1 #프로젝트 생성!
```
![alt text](image.png)


## 3 CRA로 생성한 프로젝트 실행하기
```
cd week-1 # week-1 폴더로 이동
```

```
yarn start # 프로젝트 시작 

or 

npm start # 프로젝트 시작 
```

![alt text](image-1.png)




## 4 프로젝트 구조를 살짝 뜯어보기

대략적인 흐름 
public > index.html
→ src > index.js
→ src > App.js

결국, 중요한 것은 [우리의 플레이그라운드는 ‘App.js’라는 것]



## 5 상대경로 import → 절대경로 지정하기
jsconfig.json 파일을 생성(반드시 root 경로에)
![](image-2.png)

```json
{
	"compilerOptions": {
		"baseUrl": "src"
	},
	"include": ["src"]
}
```  




<hr>

<br>
<br>





# 1-6 React Component

## 1 React Component란 
컴포넌트 개념 이해하기     

```
컴포넌트를 통해 UI를 재사용이 가능한 개별적인 여러 조각으로 나누고, 각 조각을 개별적으로 볼 수 있다.
개념적으로 컴포넌트는 JavaScript 함수와 유사하고
“props”라고 하는 임의의 입력을 받은 후, 화면에 어떻게 표시되는지를 기술하는 React 엘리먼트를 반환
```  


## 2 리액트 컴포넌트를 표현하는 두 가지 방법

- 두 가지 모두 기능상으로는 동일하지만, 공식 홈페이지에서는 함수형 컴포넌트를 사용하기를 권장   

> 함수형 컴포넌트  
```TypeScript
// props라는 입력을 받음
// 화면에 어떻게 표현되는지를 기술하는 React 엘리먼츠를 반환(return)

function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// 훨씬 쉬운 표현을 해보면 아래와 같죠.
function App () {
	return <div>hello</div>
}
```  

> 클래스형 컴포넌트  
```TypeScript
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```  


<hr>

<br>
<br>




# 1-7 부모-자식 컴포넌트

## 1 컴포넌트 안에 컴포넌트 넣기  
- 컴포넌트는 다른 컴포넌트를 품을 수 있다. 이때 다른 컴포넌트를 품는 컴포넌트를 부모 컴포넌트라고 부르고, 다른 컴포넌트 안에서 품어지는 컴포넌트를 자식 컴포넌트라고 부른다.


```TypeScript
// src/App.js
import React from "react";

function Child() {
  return <div>나는 자식입니다.</div>;
}

function App() {
  return <Child />;
}

export default App;
```




<hr>

<br>
<br>




# 1-8  JSX(JavaScript + XML)

## 1 JSX란?

```TypeScript
// JavaScript를 확장한 문법
// JavaScript의 모든 기능이 포함되어 있으며, React Element를 생성하기 위한 문법
const element = <h1>Hello, world!</h1>;
```

## 프로젝트 내에 있는 App.js를 통해 살펴보기   
> 리액트에서는 index.html 이라는 딱 하나의 html 파일만 존재하기에 **JSX 문법을 사용해서 React 요소를 만들고 DOM에 렌더링 시켜서** 그린다.

```TypeScript
// import [패키지명] from [경로] 이 형식으로 불러와요.
import React from 'react'; 
// js 파일 뿐 아니라 이미지도 가능가능!
import logo from './logo.svg';
// css? 가능!
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```


> 자바스크립트 안에서 html 태그같은 마크업을 넣어 뷰(UI) 작업을 편하게 사용가능
```TypeScript
const start_half = <div>
    <h1>안녕하세요!</h1>
    <p>시작이 반이다!</p>
  </div>;
```  

- 지금은 리액트 돔을 구성하는 건 리액트 요소! 돔을 구성하는 건 돔 요소!   



```typeScript
import React from 'react'

export default function App() {
 
 const number = 1;

const pTagStyle = {
  color : 'red',
}

  return (
    <div className='test-class'>
       <p>안녕하세요 리액트입니다.</p>
       {/* 주석을 사용하는 방법입니다. */}
       {/* 삼항연산자를 사용해 볼게요! */}
       <p style={pTagStyle}>{
       number > 10 
       ? number + '은 10 보다 크다'  
       : number + '은 10 보다 작다'}
       </p>
    </div>
  )
}
```

### 리액트 스니펫   
- 마켓에서 react snippet로 설치   
![alt text](image-3.png)  


- 빈 js파일에서 rfc, rfce 로 간단하게 아래처럼 만들 수 있음  
![alt text](image-4.png)  


<hr>

<br>
<br>


# 1-9 Props의 개요

## 1 props란?

#### **컴포넌트 끼리의 정보교환 방식!**  
부모 컴포넌트가 자식 컴포넌트에게 물려준 데이터에요! 다시 말해, **컴포넌트 간의 정보 교류 방법**입니다.  
> 1. props는 반드시 위에서 아래 방향으로 흐른다. 즉, [부모] → [자식] 방향으로만 흐른다(단방향).  
> 2. props는 반드시 읽기 전용으로 취급하며, 변경하지 않는다.    


```typeScript
import React from "react";

// div안에서 { } 를 쓰고 props.motherName을 넣어보세요.
function Child(props) {
  return <div>{props.motherName}</div>;
}

function Mother() {
  const name = "홍부인";
  return <Child motherName={name} />;
}

function GrandFather() {
  return <Mother />;
}

function App() {
  return <GrandFather />;
}

export default App;
```    




```typeScript
import React from 'react'

// props를 통해 부모 -> 자식 데이터가 전달
function Son(props) {
  return <div>{props.GrandFather}의 딸 {props.motherName}의 아들 입니다.</div>
}

//  부모 -> 자식 에게 정보를 전달했다!
function Mather(props) {
  const name = "흥부인";
  return <Son motherName = {name} GrandFather = {props.GrandFather}/>
}

function GrandFather(){
  const name = "흥할아버지";
    return <Mather GrandFather = {name} />
}

function App() {
  return (
    <div><GrandFather/></div>
  )
}

export default App
```  


## 2 prop drilling  
```
[부모] → [자식] → [그 자식] → [그 자식의 자식] 이 데이터를 받기 위해선 무려 3번이나 데이터를 내려줘야 한다.
 이걸 바로 prop drilling, props가 아래로 뚫고 내려간다. 라고 한다.
```  
  
#### 예시  
```typeScript
export default function App() {
  return (
    <div className="App">
      <FirstComponent content="Who needs me?" />
    </div>
  );
}

function FirstComponent({ content }) {
  return (
    <div>
      <h3>I am the first component</h3>;
      <SecondComponent content={content} />|
    </div>
  );
}

function SecondComponent({ content }) {
  return (
    <div>
      <h3>I am the second component</h3>;
      <ThirdComponent content={content} />
    </div>
  );
}

function ThirdComponent({ content }) {
  return (
    <div>
      <h3>I am the third component</h3>;
      <ComponentNeedingProps content={content} />
    </div>
  );
}

function ComponentNeedingProps({ content }) {
  return <h3>{content}</h3>;
}
```  

<hr>

<br>
<br>


# 1-10 Props children  
## 1 children이란?  
- 아래 예제 코드를 보면 `<User>안녕하세요</User>` 이렇게 사용하고 있는데 기존에 `<User hello='안녕하세요'>` 이렇게 props를 보내던 방식과는 조금 다릅니다. 이것이 children props를 보내는 방식입니다.  그렇다면 자식 컴포넌트에서는 어떻게 정보를 받을까요?  정보를 받는 방식은 기존과 동일합니다. 대신 그 이름이 children 으로 정해져 있습니다.  

```typescript
import React from "react";

function User(props) {
  return <div>{props.children}</div>;
}

function App() {
  return <User>안녕하세요</User>;
}
export
```  


## 2 children의 용도
> Layout 컴포넌트를 만들 때 자주 사용
- Layout 컴포넌트 안에는 header 라는 컴포넌트가 있고, header 아래에 {props.children} 를 통해서  props를 받아 렌더링 하고 있다. 

- Layout 
```typescript
import React from 'react'

function Layout(props) {
  return (
    <>
    <header style={{
        margin : "10px",
        border : "1px solid red"
    }}>
        항상 출력되는 머릿글입니다.
    </header>
    {props.children}
    </>
  )
}

export default Layout
```

- Layout 컴포넌트가 쓰여지는 모든 곳에서 <Layout>…</Layout> 안에 있는 정보를 받아서 가져올 수 있는 것
```typescript
import React from "react";
import Layout from "./components/Layout";

function App() {
  return (

    <Layout> 
      <div>여긴 App의 컨텐츠가 들어갑니다.</div>
    </Layout>
  );
}
export default App;
```  


- Layout 컴포넌트를 About 컴포넌트에 또 사용한다. 

```typescript
// src/About.js

import React from "react";
import Layout from "./components/Layout";

function About() {
  return (
    <Layout> 
      <div>여긴 About의 컨텐츠가 들어갑니다.</div>
    </Layout>
  );
}
export default About;
```


<hr>

<br>
<br>


# 1-11 Props 추출  
## 1 구조분해 할당과 Props  
>  기존 props 할당  ->  자식 컴포넌트에서 props를 받을 때 하나의 오브젝트로 받아 사용
``` typescript
function Todo(props){
	return <div>{props.todo}</div>
}
```     

<br>


> 자바스크립트의 구조 분해 할당을 이용 ->  
```typescript
function Todo({ title, body, isDone, id }){
	return <div>{title}</div>
}
```  

<br>


## 2 defaultProps    
> defaultProps란, 부모 컴포넌트에서 props를 보내주지 않아도 설정될 초기 값    

```typescript
import React from 'react';

function Child({ name }){
	return <div>내 이름은 {name} 입니다. </div>
}

// 이렇게 설정합니다.
Child.defaultProps={
	name: '기본 이름'
}

export default Child
```


<hr>


<br>
<br>

# 1-12 State  
> State란 컴포넌트 내부에서 바뀔 수 있는 값을 의미이며 UI(엘리먼트)로의 반영이 되는 것을 목적으로 사용   

## 1 State 생성  
```typescript  
import React, { useState } from 'react';

function GrandFather() {
  const [name, setName] = useState("김할아"); // 이것이 state!
  return <Mother grandFatherName={name} />;
}


//const [ value, setValue ] = useState( 초기값 )
```  

## 2 State 수정  
```typescript
import React, { useState } from 'react'

function App() {
  const [username, setUsername] = useState("");
  const [password, setPassword] = useState("");


  return (
      <div>
        아이디 : <input
         value={username}
         onChange={function(event){
          setUsername(event.target.value);
            }}></input>
        <br/>
        패스워드 : <input 
        type='password' 
        value={password} 
        onChange={function(event){
          setPassword(  event.target.value);
        }}></input>
        <br/>
        <button onClick={function(){
          alert(username + ", " + password);
          setUsername("");
          setPassword(  "");
        }}>로그인</button>
      </div>
  )
}
export default App

// state를 변경할때는 setValue(바꾸고 싶은 값) 를 사용
```


## 3 불변성이란?
- **(1) 불변성이란?**
    
    **불변성이란 메모리에 있는 값을 변경할 수 없는 것**을 말합니다. 자바스크립트의 데이터 형태중에 원시 데이터는 불변성이 있고, 원시 데이터가 아닌 객체, 배열, 함수는 불변성 없습니다.
    
- **(2) 변수를 저장하면, 메모리에 어떻게 저장이 될까?**
    
    만약 우리가 `let number = 1`  이라고 선언을 하면, 메모리에는 1 이라는 값이 저장됩니다. 그리고 `number` 라는 **변수는 메모리에 있는 1을 참조**하죠. 그리고 이어서 우리가 `let secondNumber = 1` 이라고 다른 변수를 선언을 했다고 가정해봅시다. 이때도 자바스크립트는 이미 메모리에 생성되어 있는 1이라는 값을 참조합니다. **즉, number와 secondNumber는 변수의 이름은 다르지만, 같은 메모리의 값을 바라보고 있는 것이죠. 그래서 우리가 콘솔에 `number === secondNumber` 를 하면 `true`가 보입니다.**
    
    하지만 원시데이터가 아닌 값(객체, 배열, 함수)는 이렇지 않아요. `let obj_1 = {name: ‘kim’}` 이라는 값을 선언하면 메모리에 obj_1이 저장이 됩니다. 그리고 이어서 `let obj_2 = {name: ‘kim’}` 이라고 같은 값을 선언하면 **obj_2라는 메모리 공간에 새롭게 저장**이 됩니다. **그래서 `obj_1 === obj2` 는 `false` 가 되죠.** 
    
- **(3) 데이터를 수정하면 어떻게 될까?**
    
    다시 원시데이터로 돌아와서 만약에 기존에 1이던 number를 `number = 2` 라고 새로운 값을 할당하면 메모리에서는 어떻게 될까요? **원시 데이터는 불변성이 있습니다.** 즉, 기존 메모리에 저장이 되어 있는 1이라는 값이 변하지 않고, 새로운 메모리 저장공간에 2가 생기고 number라는 값을 새로운 메모리 공간에 저장된 2를 참조하게 됩니다.  그래서 **secondNumber를 콘솔에 찍으면 여전히 1이라고 콘솔에 보입니다.** **number와 secondNumber는 각각 다른 메모리 저장공간을 참조하고 있기 때문**이죠.
    
    obj_1를 수정해봅시다. `obj_1.name = ‘park’` 이라고 새로운 값을 할당하면 어떻게 될까요? **객체는 불변성이 없습니다. 그래서 기존 메모리 저장공간에 있는 `{name: ‘kim’}` 이라는 값이 `{name : ‘park’}` 으로 바뀌어 버립니다.** 차이를 아시겠나요?
    
    **원시데이터는 수정을 했을 때 메모리에 저장된 값 자체는 바꿀 수 없고, 새로운 메모리 저장공간에 새로운 값을 저장합니다. 원시데이터가 아닌 데이터는 수정했을 때 기존에 저장되어 있던 메모리 저장공간의 값 자체를 바꿔버립니다.**
    
- **(4) 왜 리액트에서는 원시데이터가 아닌 데이터의 불변성을 지켜주는 것을 중요시할까?**
    
    리액트에서는 화면을 리레더링 할지 말지 결정할 때 state의 변화를 확인합니다. state가 변했으면 리렌더링 하는 것이고, state가 변하지 않았으면 리렌더링을 하지 않죠.
    
    그때, state가 변했는지 변하지 않았는지 확인하는 방법이 state의 변화 전, 후의 `**메모리 주소`를 비교합니다.** 그래서 만약 **리액트에서 원시데이터가 아닌 데이터를 수정할 때 불변성을 지켜주지 않고, 직접 수정을 가하면 값은 바뀌지만 메모리주소는 변함이 없게 되는것이죠.** 그래서 즉, 개발자가 값은 바꿨지만 리액트는 state가 변했다고 인지하지 못하게 됩니다. 그래서 결국 마땅히 일어나야 할 리렌더링이 일어나지 않게되죠.  


    

<hr>


<br>
<br>

# 1-13 불변성 & 순수함수
## 1 불변성이란? 
> 불변성이란 메모리에 있는 값을 변경할 수 없는 것 -> 원시 데이터는 불변성이 있고, 원시 데이터가 아닌 객체, 배열, 함수는 불변성 없다.  

```
 왜 리액트에서는 원시데이터가 아닌 데이터의 불변성을 지켜주는 것을 중요시할까? 


리액트에서는 화면을 리레더링 할지 말지 결정할 때 state의 변화를 확인한다.
 state가 변했으면 리렌더링 하는 것이고, state가 변하지 않았으면 리렌더링을 하지 않는다.

state는 `**메모리 주소`를 비교한다.

그래서 만약 **리액트에서 원시데이터가 아닌 데이터를 수정할 때 불변성을 지켜주지 않고,
직접 수정을 가하면 값은 바뀌지만 메모리주소는 변함이 없다. 

즉, state가 변했다고 인지하지 못하고 리렌더링이 일어나지 않게됩니다.
```

<br>

## 2 순수함수이란?
> 하나 이상의 인자를 받고, 인자를 변경하지 않고, 참조하여 새로운 값을 반환하는 함수 즉, 같은 input동일한 인자가 전달되면 항상 동일한 결과를 반환하는 함수(코드 블록)이다.

-  순수함수  
```typescript
// 매개변수를 복사한 값을 변경하는 순수함수
const addSixPure = (arr) => {
  // 펼침 연산자로 새로운 배열에 6 추가
  newArr = [...arr, 6];
  return newArr;
};
```


- 순수함수가 아닌 것
```typescript
const num_arr = [1, 2, 3, 4, 5];

// 매개변수의 값을 직접 변경하는 불순함수
const addSixImpure = (arr) => {
  // 매개변수에 직접 6 추가
  arr.push(6);
  return arr;
};
```

```
리액트 과정에서 갑자기 왜 순수함수?

1. 컴포넌트의 많은 루틴을  순수 함수로서 작성하기를 요구하고 있어요.
    - 컴포넌트에서 state와 props가 같으면, 항상 같은 값을 반환해야합니다.
    -  다른 Side effects를 발생시키지 않아야 합니다. (HTTP 요청, 데이터 저장, 쿠키 조작 등)

2. 컴포넌트의 상탯값은 불변 객체(Immutable Object)로 관리해야만 합니다.
    - 수정할 때에는 기존 값을 변경하는 것이 아니라, 같은 이름의 새로운 객체를 생성합니다.

3. 이를 통해, UI 개발의 복잡도를 낮추고, 버그 발생 확률도 줄입니다.
```





<hr>


<br>
<br>



# 1- 15
## 1 Component란?
- 컴포넌트는 리액트의 핵심 빌딩 블록 중 하나로 리액트에서 개발할 모든 애플리케이션은 컴포넌트라는 조각으로 구성되고 컴포넌트는 UI 구축 작업을 훨씬 쉽게 만들어준다. 
- 컴포너트는 UI 요소를 표현하는 최소한의 단위이며 화면의 특정 부분이 어떻게 생길지 정하는 선언체이다. 



#### ⭐️ DOM (명령형 프로그래밍)  
```javascript
// Hello, World! 화면에 출력하기
// 순수 javaScript 명령형 코드
const root = document.getElementById('root'); 
const header = document.createElement('h1'); 
const headerContent = document.createTextNode(
	'Hello, World!'
);

header.appendChild(headerContent); 
root.appendChild(header);
```  

⭐️ 리액트 (선언형 프로그래밍)
```javascript
// React 코드 (선언적인)
const header = <h1>Hello World</h1>; // jsx
ReactDOM.render(header, document.getElementById('root'));
```

## 2 렌더링이란?
- 리액트에서 렌더링이란, 컴포넌트가 현재 props와 state의 상태에 기초하여 UI를 어떻게 구성할지 컴포넌트에게 요청하는 작업을 의미

```
주방장과 웨이터 예시를 사용

- UI - 음식
- 컴포넌트 - 음식을 만드는 주방장
- 리액트 - 웨이터

자 그럼 렌더링이 일어나는 프로세스를 아래와 같이 설명할 수 있을 것 같습니다.

1. 렌더링 일으키는 것은 (triggering) UI를 주문하고 주방으로 전달하는 것
2. 렌더링한다는 것은 (rendering)- 주방에서 컴포넌트가 UI를 만들고 준비하는 것
3. 렌더링 결과는 실제 DOM에 커밋한다는 것은 (commit) - 리액트가 준비된 UI를 손님 테이블에 올려놓는 것
```  
![alt text](image-5.png)


## 3 렌더링 트리거가 발생 할 때
> 리액트 앱이 실행되고 첫 렌더링이 일어나면 리액트는 컴포넌트의 루트에서 시작하여 아래쪽으로 쭉 훑으며 컴포넌트가 반환하는 JSX 결과물을 DOM 요소에 반영합니다. 

1. 첫 리액트 앱을 실행했을 때
2. 현재 리액트 내부에 어떤 상태(state)에 변경이 발생했을 때. 
    - 컴포넌트 내부 state가 변경되었을 때
    - 컴포넌트에 새로운 props가 들어올 때,
    - 상위 부모 컴포넌트에서 위에 두 이유로 렌더링이 발생했을 때


## 4 리렌더링
> 첫 렌더링을 끝난 이후에 추가로 렌더링을 트리거 하려면 상태를 변경해주면 됩니다. 


컴포넌트 상태에 변화가 생기면 리렌더링이 발생합니다. 이때 여러 상태가 변경됐다면 리액트는 이를 큐 자료구조에 넣어 순서를 관리합니다.  

- 주방 예시

1. 음식점 손님이 첫 주문 이후에 갈증이 생겨 추가로 음료를 주문하거나 처음 받은 음식이 마음에 들지 않아 새로운 메뉴를 주문하는 것과 같습니다.  
2. 새로운 UI주문(**리렌더링**)이 일어나면 리액트가 변경된 내용을 주방에 있는 요리사인 컴포넌트에 전달하고 **컴포넌트**는 새로운 변경된 주문을 토대로 새로운 요리(**UI**)를 만듭니다.   
3. 새롭게 만들어진 요리(렌러딩 결과)는 리액트에 의해 다시 손님 테이블에 올려집니다(DOM에 반영 - commit phase).  

![alt text](image-6.png)



## 5 브라우저 렌더링  

브라우저의 렌더링과 리액트의 렌더링은 엄연히 다른 독립적인 프로세스입니다. 렌더링이 완료되고 React가 DOM을 업데이트한 후 브라우저는 화면을 그립니다. 이 프로세스를 "브라우저 렌더링"이라고 하지만 혼동을 피하기 위해 "페인팅"이라고도 합니다. 브라우저 렌더링에 자세히 알아보고 싶다면 [브라우저는 어떻게 동작하는가?](https://d2.naver.com/helloworld/59361)를 참고해보세요!




<hr>


<br>
<br>

# 1-18 반복되는 컴포넌트 처리하기 

## Map 사용해보기 
```typescript
import React from 'react'
import "App.css";


function Block (props) {
  return <div className='square-style'>{props.name}</div>
}

function App() {
  const testArr = ["감자", "고구마", "오이", "가지", "옥수수"]

  return (
    <>
    <div className='app-style'>
        {
          testArr.map(function(item){
              return <Block name = {item}></Block>
          })

        }
    </div>

    
  <div className='app-style'>
        {
            testArr.filter(function(item){
                return item !== "감자"
            }).map(function(item) {
              return <Block name = {item}></Block>
            })
          }

  </div>
  </>
  )
}

export default App 
```

- **1) 혹시 브라우저 콘솔에서 에러가 뜬다면?**  

![alt text](image-8.png)     
리액트에서 `map`을 사용하여 컴포넌트를 반복 렌더링 할 때는 반드시 컴포넌트에 `key`를 넣어줘야 한다.

**key가 필요한 이유**는 React에서 컴포넌트 배열을 렌더링했을 때 **각각의 원소에서 변동이 있는지 알아내려고 사용하기 때문** 만약  key가   없다면 React는 가상돔을 비교하는 과정에서 배열을 순차적으로 비교하면서 변화를 감지하려 한다. 하지만 **key가 있으면 이 값을 이용해서 어떤   변화가 일어났는지 더 빠르게 알아낼 수 있게 된다.** **즉, key값을 넣어줘야 React의 성능이 더 최적화 된다. 라는 의미**    

```javascript
 <div style={style}>
      {users.map((user) => {
        return <User user={user} key={user.id} />;
      })}
  </div>
```  

<hr>


<br>
<br>

# 1-21 컴포넌트 분리하기

#### 컴포넌트 분리 전  
- 아래 로직은 컴포넌트를 분리하기 전의 로직이다.  보면 User 컴포넌트 Button 컴포넌트 App 컴포넌트가 하나의 jsx 파일에 존재한다.
```javascript
import React, { useState } from 'react'
import "./App.css"

function App() {
  // const users = [
  //   {id: 1, age: 30, name: "송중기"},
  //   {id: 2, age: 24, name: "송강"},
  //   {id: 3, age: 21, name: "김유정"},
  //   {id: 4, age: 29, name: "구교환"}
  // ]

  const [name, setName] = useState("");
  const [age, setAge] = useState(0);

  const [users, setUsers] = useState([
    { id: 1, age: 30, name: "송중기" },
    { id: 2, age: 24, name: "송강" },
    { id: 3, age: 21, name: "김유정" },
    { id: 4, age: 29, name: "구교환" }
  ])

  const saveUsersHandler = () => {
    const newUser = { id: users.length + 1, age: age, name: name };
    setUsers([...users, newUser]); // 원래있던 user에 newUser 추가
  }

  const removeUsersHandler = (id) => {
    const totalUsers = users.filter(function (item) { return item.id !== id });
    setUsers(totalUsers === undefined ? [{}] : totalUsers); // 원래있던 user에 newUser 추가 
  }

  return (
    <div>
      이름 :<input type='text' value={name} onChange={(event) => setName(event.target.value)} />
      나이 : <input type='text' value={age} onChange={(event) => setAge(event.target.value)} />
      <Button functionValue = {saveUsersHandler}>등록</Button>
      <div className='app-style'>
        {
          users.map(function (item) {
            return <User 
            key={item.id}
            user = {item}
            removeUsersHandler = {removeUsersHandler}
            ></User>
          })

        }
      </div>
    </div>

  )
}

const User = ({user, removeUsersHandler}) => {
  console.log(user);
  return (
    <>
      <div
        key={user.id}
        className='square-style'>{user.age} - {user.name}
      </div>
      <Button functionValue = {() => removeUsersHandler(user.id)}>삭제</Button>
    </>);
}

const Button = ({functionValue, children}) => {
  return <button onClick={functionValue}>{children}</button>;
}

export default App
```

#### 컴포넌트 분리   
- 컴포넌트 폴더를 만들어 각 컴포넌트를 쪼갰다.  

![alt text](image-9.png)  

```javascript
const Button = ({functionValue, children}) => {
    return <button onClick={functionValue}>{children}</button>;
  }

  export default Button;
```

```javascript
const User = ({ user, removeUsersHandler }) => {
    console.log(user);
    return (
        <>
            <div
                key={user.id}
                className='square-style'>{user.age} - {user.name}
            </div>
            <Button functionValue={() => removeUsersHandler(user.id)}>삭제</Button>
        </>);
}

export default User;
```


#### 컴포넌트 분리 후 
```javascript
import React, { useState } from 'react'
import "./App.css"
import Button from 'componet/Button';
import User from 'componet/Users';

function App() {
  // const users = [
  //   {id: 1, age: 30, name: "송중기"},
  //   {id: 2, age: 24, name: "송강"},
  //   {id: 3, age: 21, name: "김유정"},
  //   {id: 4, age: 29, name: "구교환"}
  // ]

  const [name, setName] = useState("");
  const [age, setAge] = useState(0);

  const [users, setUsers] = useState([
    { id: 1, age: 30, name: "송중기" },
    { id: 2, age: 24, name: "송강" },
    { id: 3, age: 21, name: "김유정" },
    { id: 4, age: 29, name: "구교환" }
  ])

  const saveUsersHandler = () => {
    const newUser = { id: users.length + 1, age: age, name: name };
    setUsers([...users, newUser]); // 원래있던 user에 newUser 추가
  }

  const removeUsersHandler = (id) => {
    const totalUsers = users.filter(function (item) { return item.id !== id });
    setUsers(totalUsers === undefined ? [{}] : totalUsers); // 원래있던 user에 newUser 추가 
  }

  return (
    <div>
      이름 :<input type='text' value={name} onChange={(event) => setName(event.target.value)} />
      나이 : <input type='text' value={age} onChange={(event) => setAge(event.target.value)} />
      <Button functionValue = {saveUsersHandler}>등록</Button>
      <div className='app-style'>
        {
          users.map(function (item) {
            return <User 
            key={item.id}
            user = {item}
            removeUsersHandler = {removeUsersHandler}
            ></User>
          })

        }
      </div>
    </div>

  )
}


export default App
```