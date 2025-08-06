# Date 객체와 날짜

## 1. Date 객체를 생성하는 방법
```javascript
let date1 = new Date(); // 생성자, 현재 지금 시간을 출력하는 Date 객체로 생성
console.log(date1); // Wed Aug 06 2025 08:25:07 GMT+0900

let date2 = new Date("1998-01-01");
// let date2 = new Date("1998.01.01");
// let date2 = new Date("1998/01/01/10:10:10"); // 시간까지 넣을 수 있음
// let date2 = new Date(1997, 1, 7, 34, 59, 59);
console.log(date2); // Thu Jan 01 1998 09:00:00 GMT+0900 (한국 표준시)
```

## 2. 타임 스탬프
특정 시간이 "1970.01.01 00시 00분 00초"로 부터 몇 ms가 지났는지 의미하는 숫자값
- 위의 시간을 세계 협정 시라고 해서 UTC라고 부름
- UTC: 세계 모든 나라가 표준으로 사용하는 시간이 시작되는 지점을 말함

```javascript
let ts1 = date1.getTime();
console.log(ts1); // 1754436702414

let date4 = new Date(ts1);
console.log(date1, date4) // Wed Aug 06 2025 08:31:42 GMT+0900 (한국 표준시) Wed Aug 06 2025 08:31:42 GMT+0900 (한국 표준시) 
// 같은 시간을 저장
```

## 3. 시간 요소들을 추출하는 방법
```javascript
let year = date1.getFullYear();
let month = date1.getMonth() + 1;
let date = date1.getDate();

let hour = date1.getHours();
let minute = date1.getMinutes();
let seconds = date1.getSeconds();

console.log(
    year,
    month,
    date,
    hour,
    minute,
    seconds
); // 2025 7 6 8 31 42
```
javascript의 월은 0부터 시작
1월은 0으로 나오고 2월은 1로 나옴
getMonth 메서드로 추출한 월에는 +1 을 해줘서 사용해야함

## 4. 시간 수정하기
```javascript
date1.setFullYear(2023);
date1.setMonth(2); //2를 인수로 전달하면 3월로 인식
date1.setDate(30);
date1.setHours(23);
date1.setMinutes(59);
date1.setSeconds(59);

console.log(date1); // Thu Mar 30 2023 23:59:59 GMT+0900 (한국 표준시)
```

## 5. 시간을 여러 포맷으로 출력하기
```javascript
console.log(date1.toDateString()); // Thu Mar 30 2023
// 시간을 제외하고 날짜만 출력
console.log(date1.toLocaleString()); // 2023. 3. 30 오후 11:59:59
// 우리나라에 맞게 현지화된 형태로 시간이 문자열로 출력
```
