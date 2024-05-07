```js
function* foo(x){
	yield x + 1;
	yield x + 2;
	return x + 3;
}
```
generator由`function*`定义
除了`return`，还可以`yield`多次返回

求斐波那契数列
```js
function fib(max){
    let
    t,
    a = 0,
    b = 1,
    arr = [0, 1];
    while(arr.length < max){
        [a, b] = [b, a+b];
        arr.push(b);
    }
    return arr;
}
console.log(fib(5));//[0, 1, 1, 2, 3]
```
不使用`generator`我们只能返回一个数组
如果换成`generator`，就可以一次返回一个数，不断返回多次
```js
function* fib(max){
    let
    t,
    a = 0,
    b = 1,
    n = 0;
    while(n < max){
        yield a;
        [a, b] = [b, a + b];
        n++;
    }
    return;
}
console.log(fib(5));//fib {[[GeneratorState]]: 'suspended'}
//仅仅是创建了一个generator对象，还没有去执行它

//调用generator对象
//方法一：
let f = fib(5);
console.log(f.next());//{value: 0, done: false}
console.log(f.next());//{value: 1, done: false}
console.log(f.next());//{value: 2, done: false}
console.log(f.next());//{value: 3, done: false}
console.log(f.next());//{value: 4, done: false}
//方法二:
for(let x of fib(10)){
    console.log(x);//依次输出：0, 1, 1, ..., 34
}
```

