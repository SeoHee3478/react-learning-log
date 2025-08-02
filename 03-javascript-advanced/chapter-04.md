# 4. Spread 연산자와 Rest 매개변수

```javascript


// 1. Spread 연산자
// -> Spread: 흩뿌리다, 펼치다 라는 뜻
// -> 객체나 배열에 저장된 여러개의 값을 개별로 흩뿌려주는 역할

let arr1 = [1,2,3];
// let arr2 = [4,arr1[0], arr1[1], arr1[2],5,6];
// 위와 같은 방식으로 할당하는것은 위험하기도 하고(index 값이 변경될 수 있음) 번거로움
let arr2 = [4, ...arr1, 5, 6]
// arr1의 모든 값을 풀어서 넣어라!
console.log(arr2)

let obj = {
    a:1,
    b:2,
};

// let obj2 = {
//     a: obj1.a,
//     b: obj1.b,
//     c:3,
//     d:4,
// };

let obj2 = {
   ...obj1,
    c:3,
    d:4,
};

console.log(obj2);

function funcA(p1, p2, p3){
    console.log(p1, p2, p3)
}

funcA(...arr1);
// 1, 2, 3

// 스프레드를 사용하면 객체나 배열의 값을 간단하게 흩뿌려놓을 수 있다.


// 2. Rest 매개변수
// -> Rest는 나머지, 나머지 매개변수

function funcB(one, two, ...rest){
    // 매개변수 안에 사용했기 때문에 spread 연산자가 아니라 rest 연산자!
    // rest 뒤에는 추가적인 매개변수를 추가할 수 없음!
    // 꼭 rest변수명으로 사용하지 않아도 되고 ...만 붙이면 됨
    console.log(rest);
}

funcB(...arr1);

// [1,2,3]

```
