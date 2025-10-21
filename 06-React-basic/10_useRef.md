# useRef로 컴포넌트의 변수 생성하기

## useRef란?
- 새로운 Reference 객체를 생성하는 기능
```javascript
const refObject = useRef()
```
refObject는 컴포넌트 내부의 변수로 일반적인 값들을 저장할 수 있음

## useRef와 useState의 차이점
useRef는 useState와 비슷해보임
useRef
- Refernce 객체를 생성
- 컴포넌트 내부의 변수로 활용 가능
- 어떤 경우에도 리렌더링을 유발하지 않음

useState
- State를 생성
- 컴포넌트 내부의 변수로 활용 가능
- 값이 변경되면 컴포넌트 리렌더링

## useRef의 특징
- 컴포넌트가 렌더링하는 특정 DOM 요소에 접근하여 요소를 조작할 수 있음

```javascript
const refObject = useRef()

return(
  <div>
    <textarea
      ref={refObject}
      name="bio"
      value={input.bio}
      onChange={onChange}
    />
  </div>
)
```

