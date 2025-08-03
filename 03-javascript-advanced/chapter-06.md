 # 반복문으로 배열과 객체 순회하기

 ## 순회(iteration) 이란?
 - 배열, 객체에 저장된 여러개의 값에 순서대로 하나씩 접근하는 것을 말함

   ex) 배열 순회
   ```javascript
   let numbers = [1,2,3];
   ```

   ex) 객체 순회
   ```javascript
   let person = {
        name: "서리",
        age: 28,
        hobby: "그림그리기",
      }
   ```

  반복문을 이용한 배열, 객체 순회
  ```javascript
  for(let value of numbers){
    console.log(value);
  }

  for(let key in Object.keys(person){
    console.log(key);
  }
  ```

```javascript
// 1. 배열 순회
let arr = [1,2,3];

// 1.1 배열 인덱스
for(let i = 0; i<arr.length;i++){
    console.log(arr[i]);
    // 1
    // 2
    // 3
}

let arr2 = [4, 5, 6, 7, 8];
for(let i = 0; i<arr2.length; i++){
    console.log(arr2[i])
    // 4
    // 5
    // 6
    // 7
    // 8
}

// 1.2 for of 반복문
for(let item of arr){
    console.log(item)
    // 1
    // 2
    // 3
}
// 첫번째 반복에 item에 1, 두번째 반복에 item에 2, 세번째 반복에 item에 3

//2. 객체 순회
let person = {
    name: "서리",
    age: 28,
    hobby:"그림 그리기"
};

// 2.1 OPbject.keys 사용
// -> 객체에서 key 값들만 받아서 새로운 배열로 반환

let keys = Object.keys(person);
console.log(keys);
//  ['name', 'age', 'hobby']

for(let key of keys){
    const value = person[key];
    console.log(key, value);
    // name 서리
    // age 28
    // hobby 그림 그리기
}

// 2.2 Object.values
// -> 객체에서 value 값들만 뽑아서 새로운 배열로 반환
let values = Object.values(person);
console.log(values)
// ['서리', 28, '그림 그리기']

for(let value of values){
    console.log(value)
    // 서리
    // 28
    // 그림 그리기
}

// 2.3 for in
for(let key in person){
    console.log(key);
    // name
    // age
    // hobby
}

for(let key in person){
    const value = person[key];
    console.log(key, value);
    // name 서리
    // age 28
    // hobby 그림 그리기
}

```

주의점) for of는 배열에서만 사용할 수 있고, for in은 객체에서만 사용 가능함 

