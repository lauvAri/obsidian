异常就是一种**对象**，表示阻止正常进行程序执行的错误或者情况

异常是由**方法**抛出，方法的**调用者**捕获并处理改异常

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161022095.png)


## 免检异常和必检异常

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161034314.png)

免检异常反映出程序设计存在不可恢复的逻辑错误
## 声明异常和抛出异常

每个方法都必须声明它可能抛出的**必检异常**的类型

声明异常的关键字是`throws`，抛出异常的关键字是`throw`

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161038504.png)

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161041048.png)

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161053611.png)

## 捕获异常

- 异常处理器 exception handler
- 方法调用链
- 调用栈
- 反向传播方向寻找处理器（捕获了一个异常 catching an exception）

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161102377.png)

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161110965.png)

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161124215.png)

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161126757.png)

12.16 12.15 12.13

## 重新抛出异常

- catch块中可以抛出一个新的异常 

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161138902.png)

## `finally`子句

- 无论异常是否产生，finally子句总是会被执行
## 何时使用异常

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405161140440.png)










