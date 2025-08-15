# 첫 React App 생성하기

## React Application이란?
- React로 만든 웹 서비스는 **React App** 또는 **React Application**이라고 부름
- **Application**이라 불리는 이유:
  - 단순한 웹페이지가 아닌 **다양한 기능**을 포함한 애플리케이션 형태이기 때문

---

## React App 생성 과정
React 앱을 만드는 기본 과정:
1. **Node.js** 패키지 설정
2. **React** 라이브러리 설치
3. 기타 개발 도구 설치 및 설정  
   → 복잡한 설정 과정을 단순화하기 위해 **Vite** 사용

---

## Vite를 이용한 React App 생성

### 1. 프로젝트 생성
```bash
npm create vite@latest
```
실행하면 다음과 같은 절차가 진행됨:
```bash
> npx
> create-vite

◇  Project name:
   section04

◇  Select a framework:
   React

◇  Select a variant:
   JavaScript

◇  Scaffolding project in /path/to/section04...
└  Done. Now run:

   cd section04
   npm install
   npm run dev
```


### 2. 라이브러리 설치
```bash
npm install
```
package.json에 정의된 라이브러리들이 설치됨

---
## package.json 주요 스크립트
```json
"scripts": {
  "dev": "vite",       // 개발 서버 실행
  "build": "vite build", 
  "lint": "eslint .",  // 코드 스타일 검사
  "preview": "vite preview" // 빌드 결과 미리보기
}

```

## 실행방법
1. 개발 서버 실행
```bash
npm run dev
```
2. 브라우저에서 http://localhost:5173 접속
