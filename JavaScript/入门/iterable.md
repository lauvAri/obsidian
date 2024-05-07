```
遍历Array可以采用下标，遍历Map和Set就无法使用下标，ES6标准引入了新的iterable类型，Array Map Set 都属于该类型
```
可以用``for...of``循环遍历
``for...in``遍历的是对象的``属性名称``，而一个数组，它的每个索引被视为一个属性
```js
var m = new Map();
m.set('apple', 1);
m.set('sea', 2);
m.set('google', 7);

for(let x of m){
    console.log(x);
}
```

```
[ 'apple', 1 ]
[ 'sea', 2 ]
[ 'google', 7 ]
```