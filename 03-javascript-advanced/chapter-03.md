# 구조분해할당

// 1. 배열의 구조 분해 할당

let arr = [1,2,3];

// let one = arr[0];
// let two = arr[1];
// let three = arr[2];

let [one, two, three, four = 4] = arr;
// arr의 배열에서 인덱스 순서대로 각각 one, two, three에 할당이 됨
// four에는 undefined가 저장됨
// 기본값도 설정 가능


// 2. 객체의 구조 분해 할당
let person = {
    name: '이정환',
    age: 27,
    hobby: "데니스",
};

// let name = person.name;
// let age = person.age; 
// ...

let {name, age : myAge, hobby, extra="hello", } = person;
// 키값을 기준으로 저장할 수 있음
console.log(name, myAge, hobby, extra);
// age값은 myAge의 변수에 저장할 수 있음

// 3. 객체 구조 분해 할당을 이용해서 함수의 매개변수를 받는 방법
const func = ({name, age, hobby, extra}) => {
    console.log(name, age, hobby, extra)
}
// 객체를 넘겨받았을 때만 구조분해 할당이 가능함!
func(person);

// 일반적인 값인 10을 넘기면 사용할 수 없음
func(10);
