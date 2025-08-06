# 비동기 작업 처리하기 1. 콜백 함수

```javascript
function add(a,b, callback){
    setTimeout(()=>{
        const sum = a + b; // 3
        callback(sum);
    },3000)
}

add(1,2, (value)=>{ 
    console.log(value);
});
```

```javascript
// 음식을 주문하는 상황
function orderFood(callback){
    setTimeout(()=>{
        const food = "떡볶이";
        callback(food);
    },3000)
}

function cooldownFood(food, callback){
    setTimeout(()=>{
        const cooldownedFood = `식은 ${food}`;
        callback(cooldownedFood);
    },2000)
}

function freezeFood(food){
    setTimeout(()=>{
        const freezeFood = `냉동된 ${food}`;
        callback(freezeFood);        
    },1500);
}

orderFood((food)=>{
    console.log(food); // 3초 뒤에 떡볶이가 출력됨

    cooldownFood(food, (cooldownedFood)=>{
        console.log(cooldownedFood); // 2초 뒤에 식은 떡볶이가 출력됨
        freezeFood(cooldownedFood, (freezedFood)=>{
            console.log(freezedFood);// 1.5초 뒤에 냉동된 식은 떡볶이 출력
        })
    });
})
```
callback 함수 안에서 계속 함수를 호출하는 문법으로 코드가 작성됨 -> indent가 점점 진화됨 -> 기능이 늘어날 수록 가독성이 안좋아질 것임(callback 지옥)
promise 객체를 활용하여 콜백지옥 방지
