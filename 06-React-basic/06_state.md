# State로 상태 관리하기

## State란?

-   **State(상태)**: 사물이 현재 가지고 있는 모양이나 형편
    예) 전구 → 켜진 상태, 꺼진 상태

-   상태는 **변경 가능**하며, 상태에 따라 다른 동작을 함

    -   켜진 상태의 전구 → 전구 끄기 → 꺼진 상태의 전구
    -   꺼진 상태의 전구 → 전구 켜기 → 켜진 상태의 전구

-   React에서의 **State**

    -   현재 가지고 있는 형태나 모양을 정의하는 **동적인 값**
    -   React의 컴포넌트들은 자신만의 State를 가질 수 있음
    -   State 값에 따라 렌더링되는 UI가 달라짐
    -   State가 변경되면 컴포넌트는 다시 렌더링(리렌더링)됨
    -   하나의 컴포넌트는 여러 개의 State를 가질 수 있음

------------------------------------------------------------------------

## State 기본 예시

``` jsx
import './App.css'
import { useState } from "react";

function App() {
  const state = useState();
  console.log(state);

  return (
    <></>
  )
}

export default App
```

-   `useState`는 **배열**을 반환
    -   첫 번째 요소: state의 값
    -   두 번째 요소: 상태를 변경하는 함수 (state setter 함수)

------------------------------------------------------------------------

## 카운터 예제

``` jsx
function App() {
  const [state, setState] = useState(0);
  console.log(state);

  return (
    <>
      <h1>{state}</h1>
      <button onClick={() => setState(state + 1)}>
        +
      </button>
    </>
  )
}

export default App;
```

-   버튼 클릭 시 `state` 값이 1씩 증가\
-   React는 state 값의 변화를 감지하여 해당 컴포넌트를 **리렌더링**

------------------------------------------------------------------------

## 전구 + 카운터 예제

``` jsx
function App() {
  const [count, setCount] = useState(0);
  const [light, setLight] = useState("OFF");

  return (
    <>
      <div>
        <h1>{light}</h1>
        <button onClick={() => setLight(light === "ON" ? "OFF" : "ON")}>
          {light === "ON" ? "끄기" : "켜기"}
        </button>
      </div>

      <div>
        <h1>{count}</h1>
        <button onClick={() => setCount(count + 1)}>
          +
        </button>
      </div>
    </>
  )
}

export default App;
```

-   **전구 상태(light)** → `ON` / `OFF` 전환
-   **카운터(count)** → 버튼 클릭 시 1씩 증가

------------------------------------------------------------------------

## 왜 State를 써야 할까?

-   그냥 `let`, `const`로 선언한 변수는 값이 변경되어도 **컴포넌트가
    리렌더링되지 않음**
-   반면 `state`는 React 내부적으로 관리되어 **값 변경 시 자동으로 UI가
    갱신**됨

즉, **UI를 상태와 동기화하기 위해 State를 반드시 사용해야 함**.
