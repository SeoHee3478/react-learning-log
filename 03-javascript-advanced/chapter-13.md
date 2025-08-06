# 비동기 작업 처리하기 2. Promise

## Promise 란?
비동기 작업을 효율적으로 처리할 수 있도록 도와주는 자바스크립트의 내장 객체

## Promise는 비동기 작업을 감싸는 객체이다.
Promise 객체 > 비동기 작업(ex. setTimeout)

### Promise의 효능
- `비동기 작업 실행`
- `비동기 작업 상태 관리`
- `비동기 작업 결과 저장`
- 비동기 작업 병렬 실행
- 비동기 작업 다시 실행

## Promise의 3가지 상태
| 상태             | 설명                                 | 영어 표현       |
|------------------|--------------------------------------|-----------------|
| 대기             | 아직 작업이 완료되지 않은 상태        | Pending         |
| 성공             | 비동기 작업이 성공적으로 마무리된 상태 | Fulfilled       |
| 실패             | 비동기 작업이 실패한 상태             | Rejected        |


```
[대기 (Pending)]
      |
  +---+--------------------+
  |                        |
resolve                  reject
  |                        |
[성공 (Fulfilled)]   [실패 (Rejected)]
```

대기(pending)
- 유튜브 로딩 상태

해결(resolve)
- 영상 로딩 완료

성공(Fulfilled)
- 시청 가능

거부(reject)
- 영상 로딩 실패

실패(Rejected)
- 시청 불가능 한 상태

```javascript
function add10(num){
    const promise = new Promise((resolve, reject)=>{
    // 비동기 작업 실행하는 함수
    // executor

    setTimeout(()=>{
        if(typeof num === "number"){
            resolve(num + 10);
        }else{
            reject("num이 숫자가 아닙니다.")
        }
        //console.log("안녕"); 
        // resolve("안녕"); // resolve는 fulfilled, 인수인 "안녕"은 PromiseResult에 출력
        //reject("왜 실패했는지...")
    }, 2000)
});
return promise
}

add10(0).then((result)=>{
    console.log(result); //10
    return add10(result); 
}).then((result)=>{
    console.log(result) //20
    return add10(result);
}).then((result)=>{
    console.log(result) //30
}).catch((error)=>{
    console.log(error);
});
```
