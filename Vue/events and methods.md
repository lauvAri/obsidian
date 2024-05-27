### props
- 将父组件的数据传给子组件
- 单向绑定
- 只读
```vue
app.component('login-form',{
	//
	<custom-input v-model="email" v-bind:label="emailLabel"/>
	components:['custom-input'],
	data(){
		return{
			email:'123@example.com',
			emailLabel:'Email'
		}
	}
	//
})

app.component('custom-input',{
	props:['label','modelValue']
})
```