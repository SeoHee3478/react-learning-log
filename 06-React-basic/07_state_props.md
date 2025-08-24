# State와 Props

아래 예시는 **State**와 **Props**에 따른 컴포넌트 리렌더링을 이해하기 위한 코드

------------------------------------------------------------------------

## 초기 코드

``` jsx
const Bulb = ({ light }) => {
  console.log('light', light);
  return (
    <div>
      {light === "ON" ? (
        <h1 style={{ backgroundColor: "orange" }}>ON</h1>
      ) : (
        <h1 style={{ backgroundColor: "gray" }}>OFF</h1>
      )}
    </div>
  );
};

function App() {
  const [count, setCount] = useState(0);
  const [light, setLight] = useState("OFF");

  return (
    <>
      <div>
        <Bulb light={light} />
        <h1>{light}</h1>
        <button onClick={() => setLight(light === "ON" ? "OFF" : "ON")}>
          {light === "ON" ? "끄기" : "켜기"}
        </button>
      </div>
      <div>
        <h1>{count}</h1>
        <button onClick={() => setCount(count + 1)}>+</button>
      </div>
    </>
  );
}

export default App;
```

------------------------------------------------------------------------

## 리렌더링 조건

컴포넌트가 리렌더링 되는 조건은 3가지가 있습니다.

1.  **State 값이 변경될 때**
2.  **Props 값이 변경될 때**
3.  **부모 컴포넌트가 리렌더링 될 때**

위 코드에서 **Bulb 컴포넌트가 리렌더링 되는 이유**는 3번에 해당합니다.\
→ `count` 값이 변경되면 `App` 컴포넌트가 리렌더링 되고, 그에 따라 자식
컴포넌트인 `Bulb`도 함께 리렌더링 됩니다.

------------------------------------------------------------------------

## 불필요한 리렌더링 방지

이러한 불필요한 리렌더링을 방지하기 위해, **컴포넌트를 분리**할 수
있습니다.

------------------------------------------------------------------------

## 개선된 코드

``` jsx
import './App.css';
import { useState } from "react";

const Bulb = () => {
  const [light, setLight] = useState("OFF");
  return (
    <div>
      {light === "ON" ? (
        <h1 style={{ backgroundColor: "orange" }}>ON</h1>
      ) : (
        <h1 style={{ backgroundColor: "gray" }}>OFF</h1>
      )}

      <h1>{light}</h1>
      <button onClick={() => setLight(light === "ON" ? "OFF" : "ON")}>
        {light === "ON" ? "끄기" : "켜기"}
      </button>
    </div>
  );
};

const Counter = () => {
  const [count, setCount] = useState(0);
  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>+</button>
    </div>
  );
};

function App() {
  return (
    <>
      <Bulb />
      <Counter />
    </>
  );
}

export default App;
```

------------------------------------------------------------------------

## 정리

-   `App` 안에 `Bulb`와 `Counter`가 함께 있으면, `count` 값이 변할 때
    `Bulb`도 불필요하게 리렌더링 됨.
-   `Bulb`와 `Counter`를 각각 **독립적인 컴포넌트**로 분리하면, 서로
    영향을 주지 않고 독립적으로 동작 가능.
