# 자료형

## 자료형이란?
자료형(Type) = 집합
동일한 속성이나 특징을 가진 원소들을 묶은 것

## JavaScript의 자료형(Data Type)

| 구분     | 세부 항목            | 하위 항목           |
|----------|----------------------|---------------------|
| 원시 타입 | Number               |                     |
|          | String               |                     |
|          | Boolean              |                     |
|          | Null                 |                     |
|          | Undefined            |                     |
| 객체 타입 | Object               | Array               |
|          |                      | Function            |
|          |                      | RegExp              |

```javascript
// 1. Number Type
let num 1 = 27;
let num2 = 1.5;
let num3 = -20;

let inf = Infinity;
let mInf = -Infinity;

let nan = Nan;

// 2. String Type
let myName = "전서희";
let myLocation = "천안";
let introduce = myName + myLocation;

let introduceText = `${myName}은 ${myLocation}에 거주합니다.`

// 3. Boolean Type
let isSwitchOn = true;
let isEmpty = false;

// 4. Null Type (아무것도 없다)
let empty = null;

// 5. Undefined Type
let none;
```

null은 개발자가 명시적으로 "빈 값" 또는 "없음"을 표현할 때 사용하고,
undefined는 변수는 선언되었지만 아직 값이 할당되지 않은 상태를 의미
