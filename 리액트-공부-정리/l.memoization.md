# 1. memoization란?
- 리액트에서 리렌더링이 빈번하게 발생하는데 그 만큼 비용이 발생하는 것이기 때문에 불필요한 렌더링이 발생하지 않도록 최적화하는 것
```
⭐ memoization의 대표적이 방법

1. memo(React.memo) : 컴포넌트를 캐싱
2. useCallback : 함수를 캐싱
3. useMemo : 값을 캐싱
```


# 2. memo(React.memo) 란?
부모 컴포넌트가 리렌더링되면 자식 컴포넌트도 전부 리렌더링 되지만 불필요한 경우 자식컴포넌의 리렌더링을 막아야하는데 memo를 사용해서 막을 수 있습니다.  

### **사용법**  
> 리렌더링을 막고싶은 컴포넌트의 export구문에서 React.memo()로 감싸주면된다.  
```jsx
export default React.memo(Box1);
```  


# 3. useCallback 란?
useCallback은 함수 자체를 메모이제이션하는 훅이다.

> 왜 함수 굳이 메모이제이션 하는 걸까?
아래와 같은 함수가 있고 이 함수를 자식 컴포넌트에 props로 넘겨주었다고 가정할 경우 부모가 리렌더링 되면 testFunction에 함수가 재 할당되어 주소값이 변경된다. 즉, 자식에게 props로 준 객체의 주소가 변경되었으므로 자식이 리렌더링이 된다.
```
const testFunction = () => {
  console.log("test")
};
```


### **사용법**    
🟢 **기본 사용법**  
> useCallback의 인자로 함수를 메모이제이션할 함수를 넣어주면 된다.  
```
⭐ initCount를 메모이제이션을 할 경우 부모 컴포넌트가 리렌더링 되더라도 주소값은 그대로 이기때문에
   initCount를 사용하고 있는 자식컴포넌트가 리렌더링되지 않는다.
```  
```jsx 
const initCount = useCallback(() => {
  setCount(0);
}, []);
```


🟢 **의존성 배열을 사용하는 방법**  
> 의존성배열에 값을 넣었다면 해당 값이 변경될 때마다 리렌더링된다.  
```jsx
// count를 초기화해주는 함수
const [count, setCount] = useState(0);

const initCount = useCallback(() => {
  setCount(0);
}, [count]);

```

# 4. useMemo란
맨 처음 해당 값을 반환할 때 그 값을 특별한 곳(메모리)에 저장하고 필요할 때 마다 다시 함수를 호출해서 계산하는게 아니라 이미 저장한 값을 단순히 꺼내와서 쓸 수 있도록 캐싱을 하는 훅이다.

### **사용법**   
🟢  **기본 사용법**  
>  이렇게 1000000000번 반복하는 함수가 있고 heavyWork() 함수를 사용하면 느릴 것 이다. 
```jsx
  const heavyWork = () => {
    for (let i = 0; i < 1000000000; i++) {}
    return 100;
  };

```  

> `useMemo()`의 인자로 해당 함구를 넣어주고 의존성배열을 빈값으로 넣어주면 `value`는 200으로 캐싱된 값을 얻을 수 있다. 
```jsx
 const heavyWork = () => {
    for (let i = 0; i < 1000000000; i++) {}
    return 100;
  };

const value = useMemo(() => heavyWork(), [])
```

🟢 **의존성 배열을 사용하는 방법** 
> `count` 를 의존성배열이 넣어줬다면 `count` 값이 변경될 때마다 heavyWork()함수를 호출한다.
```jsx
const [count, setCount] = useState(0);

 const heavyWork = () => {
    for (let i = 0; i < 1000000000; i++) {}
    return 100;
  };

const value = useMemo(() => heavyWork(), [count])
```














