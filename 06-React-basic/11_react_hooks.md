# React Hooks

## React Hooks란?
React Hooks는 **클래스 컴포넌트의 기능을 함수 컴포넌트에서도 사용할 수 있게 도와주는 메서드들**

### 🔹 2017년도 이전의 React.js
**Class 컴포넌트**
- 모든 기능(State, Ref 등)을 이용할 수 있음  
- 문법이 다소 복잡함

**Function 컴포넌트**
- UI 렌더링만 가능  
- 문법은 간결하지만 기능 제약이 있음

### 💡 Hooks의 등장 배경
함수형 컴포넌트의 간결한 문법을 유지하면서 클래스 컴포넌트의 기능을 활용하기 위해 **React Hooks**가 등장
오늘날 대부분의 React 개발은 함수형 컴포넌트와 Hooks를 기반으로 함

---

## 주요 Hook 예시
| Hook | 설명 |
|------|------|
| `useState` | State 기능을 가져옴 |
| `useRef` | Reference 기능을 가져옴 |

모든 Hook 이름은 **`use` 접두사**로 시작
또한, **Hook은 함수 컴포넌트 내부에서만 호출 가능**하며,  
**조건문이나 반복문 내부에서는 호출할 수 없음.**

---

## Custom Hook (나만의 훅)
React에서는 직접 나만의 Hook을 만들 수도 있음

### ✅ 예시 1. `useInput` Hook

```javascript
// useInput.jsx
import { useState } from "react";

function useInput() {
  const [input, setInput] = useState("");

  const onChange = (e) => {
    setInput(e.target.value);
  };

  return [input, onChange];
}

export default useInput;
```

---

### ✅ 예시 2. `useInput` 사용하기

```javascript
// App.jsx
import useInput from "./../hooks/useInput";

const HookExam = () => {
  const [input, onChange] = useInput();
  const [input2, onChange2] = useInput();

  return (
    <div>
      <input value={input} onChange={onChange} />
      <input value={input2} onChange={onChange2} />
    </div>
  );
};

export default HookExam;
```

---

## ⚠️ Hook 사용 시 주의사항
1. **함수 컴포넌트 또는 커스텀 훅 내부에서만 호출 가능**
2. **조건문, 반복문 내에서 호출 불가**  
   → Hook 호출 순서가 달라질 수 있음
3. **Custom Hook 제작 시 이름 앞에 `use` 접두사 필수**

---

> 📘 정리: React Hooks는 함수형 컴포넌트를 더 강력하고 유연하게 만들어주는 핵심 기능으로, 재사용성과 유지보수성을 높이는 데 큰 역할을 합니다.
