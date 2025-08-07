section1 - chapter11
# 함수 표현식과 화살표 함수
## 1. 함수 표현식
```javascript
function funcA(){// 함수선언문
    console.log("funcA");
}

let varA = funcA(); // 함수 표현식
console.log(varA);

let varB = function funcB(){
    console.log("funcB");
}

varB();
funcB(); // 오류 발생

let varB = function (){ // 익명함수
    console.log("funcB");
} 

varB();
```

## 2. 화살표 함수
함수를 이전보다 더 간결하고 빠르게 생성해줄 수 있는 js 문법
```javascript
let varC = (value) => {
    console.log(value);
    value + 1
};


console.log(varC(10));

```
