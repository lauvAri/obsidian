```vue
<script>
    export default{
        name: 'Person',
        
        setup(){
            //console.log("@@"+this);
            //setup函数中的this是undefined
            //数据
            let name = '张三';//此时name不是响应式的
            let age = 18;//此时age不是响应式的
            let tel = '13889898989';//此时tel 不是响应式的

            //方法
            function changeName(){

                //vue3中setup里面不能用this
                name = "zhang-san";//这样修改，页面是没有变化的
                console.log(name);//name确实改了，但name不是响应式的
            }
            function changeAge(){
                age += 1;
                console.log(age);
            }
            function showTel(){
                alert(tel);
            }

            //返回一个对象
            //将数据、方法交出去，模板才能使用
            return {age:age, name: name, changeAge, changeName, showTel};
            //可简写为{age, name}            
        }
    }
</script>
```
