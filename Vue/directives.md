### v-model
- 负责监听用户的输入事件以更新数据
- 背后有两个操作
	1. v-bind绑定value属性的值
	2. v-on绑定input事件监听到函数中，函数会获取最新的值赋值到绑定的属性中
```vue
<input v-model="searchText">
```
等价于
```vue
<input :value="searchText" @input="searchText = $event.target.value">
```