- Asynchronous JavaScript and XML（异步的JavaScript和XML）
- Web运行的原理：一次HTTP请求对应一个页面
- 如要让用户留在当前页面中，同时发出新的HTTP请求，就需要javaScript发送这个请求，接收到数据后，再用javaScript更新页面。
- 通过在后台与服务器进行少量数据交换，使网页实现异步更新，在不重新加载整个网页的情况下，对部分内容进行更新。
- AJAX请求是异步执行的，要通过回调函数获得响应
- 写AJAX依靠`XMLHttpRequest`对象
## 异步编程
- 步骤在一个控制流序列中按顺序执行：同步（Synchronous, sync）
- 异步（async）执行不再按照原有的顺序关系
- 一般用子线程来完成一些消耗时间比较长的事情
- 子线程一旦发射就会与主线程失去同步，我们无法确定它的结束
- 回调函数是在我们启动一个异步任务时就告诉它：等完成这个任务后要干什么
```
<script>
	function print(){
		document.getElementById("demo").innerHTML = "RUNOOB!";
	}
	setTimeout(print, 3000);
</script>
```
等价于下面这段代码
```
setTimeout(function(){
	document.getElementById("demo").innerHTML = "RUNOOB!";
}, 3000);
```
## 创建XMLHttpRequest对象
`var xmlhttp = new XMLHttpRequest();`
## 向服务器发送请求
`xmlhttp.open("GET", "url", true);`
`xmlhttp.send();`
open(method, url, async)
- 规定请求的类型、URL以及是否异步处理请求
- method: 请求的类型，GET或者POST
- url：文件在服务器上的位置
- async：true（异步）或false（同步）
send(string)
- 将请求发送到服务器
- string：仅用于POST请求
## GET POST
GET更简单也更快，但是以下情况，使用POST
- 不愿使用缓存文件（更新服务器上的文件或数据库）
- 向服务器发送大量数据（POST 没有数据量限制）
- 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠