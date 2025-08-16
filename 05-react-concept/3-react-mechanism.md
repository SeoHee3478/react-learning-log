# 🚀 React App 구동 원리 살펴보기

## 1. Vite와 React App 실행
Vite로 생성한 React App에는 **내장 Web Server**가 포함  
`npm run dev` 명령어를 실행하면 이 서버가 가동

```bash
 Local:   http://localhost:5173/
```

위 주소로 접속하면 현재 실행 중인 React Web Server에 접근 가능

---

## 2. 로컬호스트(Localhost)와 포트(Port)
- **로컬호스트(Localhost)** → 내 컴퓨터 자체를 의미 
- **포트 번호(Port Number)** → 같은 컴퓨터에서 여러 개의 서버를 실행할 때,  
  각각의 서버를 구분하기 위해 사용

예시:
- React Server → `5173`
- PHP Server → `3344`

즉, 단순히 `localhost`만 사용하면 어떤 서버인지 구분할 수 없으므로 포트 번호 필수

---

## 3. React 엔트리 포인트: `main.jsx`

```jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
  </StrictMode>,
)
```

### 코드 해설
- **`createRoot`**  
  - 전달받은 요소(`root`)를 React의 Root로 설정 
- **`render` 메서드**  
  - `App` 컴포넌트를 실제 DOM에 렌더링  
- **`App`**  
  - `App.js(App.jsx)` 파일을 의미하며, React App의 시작점

---

## 요약
- `npm run dev` → Vite 내장 서버 실행  
- `localhost:포트번호` → 서버 접속 주소  
- `main.jsx` → React 앱이 처음으로 실행되는 진입점  
