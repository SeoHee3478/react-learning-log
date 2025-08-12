#  Node.js 

## 1. Node.js를 왜 배워야 하나요?
- **React.js**는 Node.js를 기반으로 동작하는 기술이기 때문
- React.js, Next.js, Vue.js, Svelte 모두 Node.js 기반

---

## 2. Node.js란?
- **JavaScript 실행 환경(런타임)**
- Chrome **V8 JavaScript 엔진**으로 빌드된 JavaScript 런타임
- 브라우저 밖에서도 JavaScript를 실행할 수 있도록 해준다.

---

## 3. Node.js는 왜 만들었을까?

### JavaScript의 역사
- 원래 **웹 페이지 내부의 단순한 기능**을 위해 만들어짐
- 유연하고 생산성이 높아짐에 따라 활용 범위 확대

💡 **활용 예시**
- **웹 서버**: 넷플릭스, 에어비앤비
- **모바일 앱**: 페이스북, 인스타그램
- **데스크톱 앱**: 슬랙, 디스코드

📊 **2023년 프로그래밍 언어 사용량 조사**  
→ JavaScript는 가장 많은 개발자가 사용하는 언어

---

# ⚡ Node.js 사용하기

## 프로젝트와 패키지
- **프로젝트**: 특정 목적을 가진 프로그램 단위
- **패키지**: Node.js에서 사용하는 프로그램 단위

### 프로젝트 초기화
```bash
npm init
```

### JS 파일 실행
```bash
node index.js
```

### 매번 실행 명령어 입력이 번거로울 때
`package.json`에 스크립트 추가:
```json
"scripts": {
  "start": "node src/index.js"
}
```

이제 실행:
```bash
npm run start
```

---

# 📦 Node.js 모듈 시스템

## 1. 모듈이란?
- 기능별로 코드를 나눈 파일 단위
- 예:
  - 회원 관리 (`user.js`)
  - 장바구니 (`cart.js`)
  - 결제 (`payment.js`)

---

## 2. 모듈 시스템 종류
- **CommonJS (CJS)**
- **ES Module (ESM)**
- AMD
- UMD

---

## 3. CommonJS 예시
**math.js**
```js
function add(a, b) {
  return a + b;
}

function sub(a, b) {
  return a - b;
}

module.exports = { add, sub };
```

**index.js**
```js
const { add, sub } = require("./math");

console.log(add(1, 2)); // 3
console.log(sub(1, 2)); // -1
```

---

## 4. ES Module 예시

### 설정
`package.json`에 추가:
```json
"type": "module"
```

**math.js**
```js
export function add(a, b) {
  return a + b;
}

export function sub(a, b) {
  return a - b;
}

export default function multiply(a, b) {
  return a * b;
}
```

**index.js**
```js
import { add, sub } from "./math.js";
import mul from "./math.js";

console.log(add(1, 2)); // 3
console.log(sub(1, 2)); // -1
console.log(mul(3, 5)); // 15
```

⚠ **주의**: ES Module에서는 import 시 반드시 **확장자까지** 적어야 함.


