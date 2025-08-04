# 배열 메서드 1. 요소 조작

## 6가지의 요소 조작 메서드

## 1.push
배열의 맨 뒤에 새로운 요소를 추가하는 메서드

```javascript
let arr1 = [1,2,3];
const newLength = arr1.push(4, 5, 6, 7);

console.log(arr1);
console.log(newLength) //push method 이후에 변경된 메서드인 7이 나오게 됨(push의 return 값은 배열 전체의 길이)
```

## 2. pop
배열의 맨 뒤에 있는 요소를 제거하고, 반환

```javascript
let arr2 = [1,2,3];
const popedItem = arr2.pop();

console.log(popedItem); // 3 
console.log(arr2); // [1, 2]
// pop의 제거된 요소를 반환
```

## 3. shift
배열의 맨 앞에 있는 요소를 제거, 반환

```javascript
let arr3 = [1, 2, 3];
const shiftedItem = arr3.shift();
console.log(shiftedItem, arr3); // 1 [2, 3]
```

## 4. unshift
배열의 맨 앞에 새로운 요소를 추가하는 메서드

```javascript
let arr4 = [1,2,3];
const newLength2 = arr4.unshift(0);
console.log(newLength2, arr4); // (4) [0, 1, 2, 3]
```
- shift와 unshift는 push나 pop보다는 비교적 느리게 동작하게 됨
- 되도록 push, pop을 통해서 해결하는 것을 권장

## 5. slice
마치 가위처럼 배열의 특정 범위를 잘라내서 새로운 배열로 반환
```javascript
let arr5 = [1, 2, 3, 4, 5];
let sliced = arr5.slice(2, 5);
let sliced2 = arr5.slice(2);
let sliced3 = arr5.slice(-1);
console.log(sliced); // [3, 4, 5] 
console.log(arr5) // [1, 2, 3, 4, 5]
console.log(sliced2) // [3, 4, 5]
console.log(sliced3) // [5]
```
- slice 메서드를 사용해도 원본배열은 변하지 않음

## 6. concat
두개의 서로 다른 배열을 이어 붙여서 새로운 배열을 반환
```javascript
let arr6 = [1, 2];
let arr7 = [3, 4];
let concatedArr = arr6.concat(arr7); 
console.log(concatedArr) // [1, 2, 3, 4]
```
