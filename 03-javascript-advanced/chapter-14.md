# 비동기 작업 처리하기 3. Async&Await
## async
함수를 비동기 함수로 만들어주는 키워드
함수가 프로미스를 반환하도록 변환해주는 키워드

```javascript
async function getData(){
    return {
        name: "서리",
        id: "haseulla",
    }
}
console.log(getData()) // promise가 반환됨

async function getData(){
    return new Promise((resolve, reject)=>{
        setTimeout(()=>{
            resolve({
                name: "서리",
                id:"haseulla",
            })
        },1500);
    });
}
```
async는 프로미스를 반환하지 않는 함수에 붙어서 자동으로 해당함수를 비동기로 작동하도록 변환하는 기능을 함

## await
async 함수 내부에서만 사용이 가능한 키워드
비동기 함수가 다 처리되기를 기다리는 역할

```javascript
function printData(){
    getData().then((result)=>{
        console.log(result);
    });
}

async function printData(){
    const data = await getData();
}
// then 메서드를 쓰지 않아도 알아서 getData가 반환하는 promise가 종료되기를 기다림
printData();
```


