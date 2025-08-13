# 📘 React.js 개론

## React.js란?
- **Meta**(구 Facebook)가 개발한 **오픈소스 JavaScript 라이브러리**
- 대규모 웹 서비스의 **UI를 더 편하게 개발**하기 위해 만들어진 기술

**사용 예시**: Netflix, Facebook, Instagram, Notion

---

## 🔹 React의 기술적인 특징
1. **컴포넌트를 기반으로 UI를 표현**한다.
2. **화면 업데이트 구현이 쉽다.**
3. **화면 업데이트가 빠르게 처리된다.**

---

### 1. 컴포넌트를 기반으로 UI를 표현
- 예: `Header.js`, `Main.js`, `Footer.js`
- **레고 조립하듯** 여러 개의 컴포넌트로 하나의 페이지를 구성 가능
- 컴포넌트를 사용하지 않으면 **중복 코드 발생** → 페이지 수 증가 시 수정이 어려움
- 유지보수 측면에서 유리

---

### 2. 화면 업데이트 구현이 쉽다

#### 📌 업데이트란?
- 사용자의 행동(클릭, 드래그 등)에 따라 **웹페이지가 스스로 바뀌어 상호작용**하는 것

#### 선언형 vs 명령형 프로그래밍
- **선언형**: 과정은 생략하고 **목적만 명시**, 코드가 간결
- **명령형**: 목적을 이루기 위한 모든 과정을 설명, 코드가 길고 복잡

#### React의 방식
- 각 컴포넌트는 State(상태)를 가질 수 있음
- **State 변경** → 자동으로 **렌더링 결과 변경**
- 복잡한 동작 정의 없이 **변수 값 변경만으로 화면 업데이트 가능**

---

### 3. 화면 업데이트가 빠르게 처리된다

#### 💡 사전 지식 필요
- 브라우저 동작 방식
- HTML/CSS 렌더링 과정
- 화면 업데이트 처리 방식

#### 브라우저 렌더링 과정 (Critical Rendering Path)
1. HTML → **DOM** 생성  
   CSS → **CSSOM** 생성
2. DOM + CSSOM → **Render Tree** 생성  
   - DOM: 요소의 위치, 배치, 모양 정보  
   - CSSOM: 스타일 정보
3. **Layout(배치)** → **Painting(그리기)**

#### 화면 업데이트 과정
- JavaScript로 **DOM 수정** 시 Render Tree → Layout → Painting 재실행
- **Layout(Reflow)**, **Painting(Repaint)** 과정은 매우 오래 걸림

---

### 🚨 성능 비교 예시

**Bad Practice**: DOM을 3000번 수정
```html
<script>
  function onClick() {
    const $ul = document.getElementById("ul");
    for (let i = 0; i < 3000; i++) {
      $ul.innerHTML += `<li>${i}</li>`;
    }
  }
</script>
<body>
  <button onclick="onClick()">리스트 추가하기</button>
  <ul id="ul"></ul>
</body>
```
- 성능: **4,500ms**

**Good Practice**: DOM 수정 1번
```html
<script>
  function onClick() {
    const $ul = document.getElementById("ul");
    let list = "";
    for (let i = 0; i < 3000; i++) {
      list += `<li>${i}</li>`;
    }
    $ul.innerHTML = list;
  }
</script>
<body>
  <button onclick="onClick()">리스트 추가하기</button>
  <ul id="ul"></ul>
</body>
```
- 성능: **250ms** (약 22배 개선)

✅ **DOM 수정 횟수를 최소화**하고, 가능한 **한 번에 반영**하는 것이 핵심

---

## ⚡ React의 해결책: Virtual DOM

**Virtual DOM**이란?
- **DOM을 자바Script 객체로 흉내낸 복제판**
- 업데이트 발생 시 **실제 DOM 수정 전**, Virtual DOM에 먼저 반영
- 변경 사항을 모아 **한 번에 실제 DOM 수정** → 성능 최적화
