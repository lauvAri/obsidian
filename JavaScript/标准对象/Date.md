当前时间是浏览器**从本机操作系统获取的时间**，所以不一定准确，因为用户可以把当前时间设定为任何值。
```js
//获取系统当前时间
var now = new Date();
console.log(now);//Sat May 04 2024 09:35:16 GMT+0800 (中国标准时间)
console.log(now.getFullYear());//2024
console.log(now.getMonth());//5
console.log(now.getDate());//4
console.log(now.getDay());//4
console.log(now.getHours());//9
console.log(now.getMinutes());//41
console.log(now.getSeconds());//18
console.log(now.getMilliseconds());//918(毫秒数)
console.log(now.getTime());//1714786878918(时间戳，number)
```

```js
//创建指定日期和时间
var d = new Date(2015, 5, 17, 20, 15, 30, 123);
console.log(d);//Wed Jun 17 2015 20:15:30 GMT+0800 (中国标准时间)
```
JavaScript的月份范围用整数表示是0~11，`0`表示一月，`1`表示二月……，所以要表示6月，我们传入的是`5`！

第二种创建一个指定日期和时间的方法是解析一个符合[ISO 8601](http://www.w3.org/TR/NOTE-datetime)格式的字符串：
![Pasted image 20240504095024](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405080033944.png)
```js
//创建指定日期和时间二（ISO 8601）
var date = new Date('2015-06-17T20:15:30+08:00');
console.log(date);//Wed Jun 17 2015 20:15:30 GMT+0800 (中国标准时间)
console.log(data.getMonth);//5注意使用getMonth得到的是0~11的整数
```

## 时间戳

时间戳是一个自增的整数，它表示从1970年1月1日零时整的GMT时区开始的那一刻，到现在的毫秒数。假设浏览器所在电脑的时间是准确的，那么世界上无论哪个时区的电脑，它们此刻产生的时间戳数字都是一样的，所以，时间戳可以精确地表示一个时刻，并且与时区无关。

