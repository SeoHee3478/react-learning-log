# 배열 메서드 3. 배열 변형

## 5가지의 배열 변형 메서드
### 1. filter
기존 배열에서 조건을 만족하는 요소들만 필터링하여 새로운 배열로 변환

```javascript
let arr1 = [
  {name:"홍길동", hobby:"그림그리기"},
  {name:"김남길", hobby:"운동하기"},
  {name:"김효빈", hobby:"운동하기"},
];

const exercisePeople = arr1.filter((item)=>{
  if(item.hobby ==='운동하기') return true;
});
```
운동하기에 해당하는 요소들만 묶어서 새로운 배열로 반환
filter 메서드는 카테고리별 필터에 필수적으로 사용함

### 2. map
배열의 모든 요소를 순회하면서, 각각 콜백함수를 실행하고 그 결과값들을 모아서 새로운 배열로 반환
```javascript
let arr2 = [1,2,3];
const mapResult1 = arr2.map((item, idx, arr)=>{
  return item * 2;
});

console.log(mapResult) // [2,4,6]

let names = arr1.map((item)=>item.name);
console.log(names) //  ['홍길동', '김남길', '김효빈']
```

### 3. sort
배열을 사전순으로 정렬하는 메서드
```javascript
let arr3 = ["b", "a", "c"];
arr3.sort();

console.log(arr3);

let arr3a = [10, 3, 5];
arr3a.sort();

console.log(arr3); // [10 3, 5]
```
sort 메소드는 숫자의 대소관계로 정렬하는 것이 아닌 사전순으로 정리함
대소관계로 정렬을 하려면 다음과 같이 작성해야함
```javascript
let arr3a = [10, 3, 5];
arr3a.sort((a,b)=>{
  if(a > b){
   // b 가 a 앞에 와라 
    return 1; -> b,a 배치
  }else if(a<b){
    return -1; // a,b 배치
  }else {
    // 두 값의 자리를 바꾸지 마라
    return 0;
  }
})
```

### 4.toSorted (가장 최근에 추가된 최신 함수)
정렬된 새로운 배열을 반환하는 메서드
```javascript
let arr5 = ["c", "a", "b"];
const sorted = arr5.toSorted();

console.log(arr5); //['c', 'a', 'b']
console.log(sorted); //['a', 'b', 'c']
```

### 5. join
배열의 모든 요소를 하나의 문자열로 합쳐서 반환하는 메서드
```javascript
let arr6 = ["hi", "im", "winterlood"];
const joined = arr6.join(" ");
console.log(joined);
```
