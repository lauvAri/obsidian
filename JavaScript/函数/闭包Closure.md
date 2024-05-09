如果不需要立刻求和，而是在后面的代码中，根据需要再计算怎么办？可以不返回求和的结果，而是返回求和的函数！

```js
function lazy_sum(arr) {
    var sum = function () {
        return arr.reduce(function (x, y) {
            return x + y;
        });
    }
    return sum;
}
```

当我们调用`lazy_sum()`时，返回的并不是求和结果，而是求和函数：

```js
var f = lazy_sum([1, 2, 3, 4, 5]); // function sum()
```

调用函数`f`时，才真正计算求和的结果：

```
f(); // 15
```
请再注意一点，当我们调用`lazy_sum()`时，每次调用都会返回一个新的函数，即使传入相同的参数：

```js
var f1 = lazy_sum([1, 2, 3, 4, 5]);
var f2 = lazy_sum([1, 2, 3, 4, 5]);
f1 === f2; // false
```
`f1()`和`f2()`的调用结果互不影响。

## 计数器
```js
function count(){
    var cnt = 0;
    return ()=>{
        cnt+=1;
        console.log(cnt);
    };
}
var cnt = count();
cnt();
cnt();
cnt();
```

## adder
```js
function makeAdder(x){
    return (y)=>{
        return x + y;
    }
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));//7
console.log(add10(2));//12
```
`add5` 和 `add10` 都是闭包。它们共享相同的函数定义，但是保存了不同的词法环境。在 `add5`的环境中，`x` 为 5。而在 `add10` 中，`x` 则为 10。
## 实用的闭包
- 闭包允许将函数与其所操作的某些数据（环境）关联起来。这显然类似于面向对象编程。在面向对象编程中，对象允许我们将某些数据（对象的属性）与一个或者多个方法相关联。
- 通常使用只有一个方法的对象的地方，都可以使用闭包
```html
	<p>some paragraph text</p>
    <h1>some heading 1</h1>
    <h2>some heading 2</h2>
    <a href="#" id = "size-12">12</a>
    <a href="#" id = "size-14">14</a>
    <a href="#" id = "size-16">16</a>
    <script>
        function makeSizer(size){
            return ()=>{
                document.body.style.fontSize = size + "px";
            };
        }

        var size12 = makeSizer(12);
        var size14 = makeSizer(14);
        var size16 = makeSizer(16);

        document.getElementById('size-12').onclick= size12;
        document.getElementById('size-14').onclick= size14;
        document.getElementById('size-16').onclick= size16;
    </script>
```
![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405082033267.png)
我们按下对应的数字，页面的字体大小会相应地改变
