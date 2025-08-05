# 배열 메서드 2. 순회와 탐색

## 1. forEach
모든 요소를 순회하면서, 각각의 요소에 특정 동작을 수행시키는 메서드
```javascript
let arr1 = [1, 2, 3]; // 3회 호출

arr1.forEach(function(item, idx, arr){
    console.log(idx, item * 2); // [2, 4, 6]
});

let doubledArr = [];
arr1.forEach((item)=>{
    doubledArr.push(item*2);
})

console.log(doubledArr)
```

## 2. includes
배열에 특정 요소가 있는지 확인하는 메서드
```javascript
let arr2 = [1, 2, 3];
let isInclude = arr2.includes(3);
console.log(isInclude); // true
```

## 3. indexOf
특정 요소의 인덱스(위치)를 찾아서 반환하는 메서드
```javascript
let arr3 = [1, 2, 3];
let index = arr3.indexOf(2);
console.log(index); // 1
```

## 4. findIndex
모든 요소를 순회하면서, 콜백함수를 만족하는 특정 요소의 인덱스(위치)를 반환하는 메서드
```javascript
let arr4 = [1, 2, 3];
const findIndex = arr4.findIndex((item)=>{
    if(item % 2 !== 2) return true;
}); 

console.log(findIndex); // 0

const findIndex2 = arr4.findIndex((item)=>{
    if(item === 999) return true;
}); 

console.log(findIndex2); // -1
```

findIndex가 중요한 이유: indexOf는 객체타입일 때 정확하게 못찾아냄

```javascript
let objectArr = [
    {name:"전서리"},
    {name:"오갱준"},
]

console.log(objectArr.indexOf({name:"전서리"})) // -1 -> 못찾는 문제
console.log(objectArr.findIndex((item)=>item.name==="전서리")) // 0
```

indexOf는 기본적으로 얕은 비교로 동작되기 때문에 못찾음
은비교? === 동등비교 연산자를 이용해서 비교하는 것

객체는 참조값을 기준으로 비교가 되기 때문에 프로퍼티를 기준으로는 비교가 안됨
indexOf를 사용해서는 배열에서 특정 객체값이 존재하는지 찾아낼 수 없음
이럴 때 findIndex를 이용해야함


## 5. find
모든 요소를 순회하면서 콜백함수를 만족하는 요소를 찾는데, 요소를 그대로 반환

```javascript
let arr5 = [
    {name:"전서리"},
    {name:"오갱준"},
]

const finded = arr5.find((item)=> item.name ==="전서리");
console.log(finded); // {name:'전서리'}
```
