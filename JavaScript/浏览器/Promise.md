- ES6提供的类，更优雅地书写异步任务
- 构建Promise
```
new Promise(function(resolve, reject){
	//todo
});
```

```js
new Promise(function(resolve, reject){

    //1s后执行
    setTimeout(function(){
        console.log("first");
        resolve();
    }, 1000);
}).then(function(){
    return new Promise(function(resolve, reject){

        //4s后执行
        setTimeout(function(){
            console.log("second");
            resolve();
        }, 4000);
    })
}).then(function(){

    //3s后执行
    setTimeout(function(){
        console.log("third");
    }, 3000);
});

```
如果不采用Promise我们必须要采取“瀑布式”的写法
```js
setTimeout(function(){

    //1s后执行
    var x = document.createElement('p');
    x.innerHTML = "1s后打印first";
    const test = document.getElementById("test");
    test.appendChild(x);
    console.log("first");

    setTimeout(function(){

        //2s后执行
        var x = document.createElement('p');
        x.innerHTML = "2s后打印second";
        const body = document.getElementById("test");
        body.appendChild(x);
        console.log("second");

        setTimeout(function(){

            //3s后执行
            var x = document.createElement('p');
            x.innerHTML = "3s后打印third";
            const body = document.getElementById("test");
            body.appendChild(x);
            console.log("third");
        }, 3000);
    }, 2000);
}, 1000);

```
## 构造函数
```js
new Promise(function(resolve, rejected){
	//todo
})
```
- 构造函数接受一个函数作为参数，被称为起始函数，起始函数是同步的并会被立即执行
- 起始函数的两个参数`resolve`和`rejected`分别表示成功和失败
- Promise 构造函数返回一个 Promise 对象，该对象具有以下几个方法：
	- then：用于处理 Promise 成功状态的回调函数。
	- catch：用于处理 Promise 失败状态的回调函数。
	- finally：无论 Promise 是成功还是失败，都会执行的回调函数。
```js
const promise = new Promise((resolve, rejected)=>{

    //异步操作
    setTimeout(()=>{
        if(Math.random() < 0.5){
            resolve("success");
        } else {
            rejected("error");
        }
    }, 1000);
})

promise.then(result=>{

    //使用 then 方法处理 Promise 成功状态的回调函数
    console.log(result);
}).catch(error=>{

    //使用 catch 方法处理 Promise 失败状态的回调函数
    console.log(error);
})
```

```js
new Promise((resolve, rejected)=>{
    let a = 0, b =  1;
    if(b === 0){
        rejected("divide zero");
    } else {
        resolve(a / b);
    }
}).then(value=>{
    console.log("a / b = " + value);
}).catch(err=>{
    console.log(err);
}).finally(()=>{
    console.log("不管怎样，都要执行");
})
```
![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405081724506.png)

- resolve() 中可以放置一个参数用于向下一个 then 传递一个值，then 中的函数也可以返回一个值传递给 then
```js
new Promise((resovle, rejected)=>{
    console.log(1111);
    resovle(2222);
}).then(value=>{
    console.log(value);
    return 3333;
}).then(value=>{
    console.log(value);
    throw "An error";     
}).catch(err=>{
    console.log(err);
})
```

## Promise函数
- 返回值是Promise对象的函数
```js
////把核心部分写成一个Promise函数
function print(delay, message){
    return new Promise((resolve, reject)=>{
        setTimeout(()=>{
            console.log(message);
            resolve();
        }, delay);
    });
}
//调用
print(1000, "first").then(()=>{
    return print(4000, "second");
}).then(()=>{
    print(3000, "third");
});
```
## 异步函数
```js
function print(delay, message){
    return new Promise((resolve, reject)=>{
        setTimeout(()=>{
            console.log(message);
            resolve();
        }, delay)
    });
}
async function asyncFunc(){
    await print(1000, "first");
    await print(4000, "second");
    await print(3000, "third");
}
asyncFunc();
```
异步函数 async function 中可以使用 await 指令，await 指令后必须跟着一个 Promise，异步函数会在这个 Promise 运行中暂停，直到其运行结束再继续运行。
处理异常的机制将用 try-catch 块实现：
```js
async function asyncFunc(){
    try{
        await new Promise((resolve, reject)=>{
            throw "An error!";
        })
    } catch(err){
        console.log(err);
    }
}
asyncFunc();
```