# 🔁 콜백 함수 (Callback Function)

콜백 함수란 **자신이 아닌 다른 함수에 인수로 전달된 함수**를 의미한다.  
즉, 특정 시점에 **호출될(Callback)** 함수를 미리 전달해두는 방식이다.

---

## ✅ 기본 개념 예제

```js
function main(value) {
  value();
}

function sub() {
  console.log("sub");
}

main(sub); // sub
```

- `main` 함수는 `value`라는 함수를 인수로 받는다.
- 이때 `main(sub)`처럼 다른 함수 `sub`을 전달하면,  
  `sub`은 **콜백 함수(callback function)** 라고 부른다.

---

## 🧪 콜백 함수 예제

### 1. 기본 사용

```js
function main(value) {
  console.log(1);
  console.log(2);
  value(); // 콜백 호출
  console.log("end");
}

main(() => {
  console.log("i am sub");
});
```

📌 결과:
```
1
2
i am sub
end
```

---

### 2. 콜백 함수의 활용: 반복 처리

```js
function repeat(count, callback) {
  for (let idx = 1; idx <= count; idx++) {
    callback(idx);
  }
}

// 2배씩 출력
repeat(5, (idx) => {
  console.log(idx * 2);
});

// 3배씩 출력
repeat(5, (idx) => {
  console.log(idx * 3);
});
```

💡 `repeat` 함수는 반복 횟수와 함께 **반복마다 실행할 동작(callback)** 을 전달받는다.  
이를 통해 다양한 방식으로 반복 처리를 커스터마이징할 수 있다.

---

## 📝 요약

| 항목        | 설명                                                                 |
|-------------|----------------------------------------------------------------------|
| 정의        | 다른 함수에 인수로 전달되는 함수                                      |
| 특징        | 전달된 함수는 **나중에 호출(Callback)** 됨                           |
| 활용 예시   | 이벤트 처리, 반복 로직, 비동기 처리 (setTimeout, fetch 등)            |
| 장점        | 코드 재사용, 유연한 로직 구성, 비동기/이벤트 기반 처리에 적합         |

---

