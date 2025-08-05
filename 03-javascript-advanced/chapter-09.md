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
```

