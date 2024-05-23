
> [!abstract] 
> 使用String类处理定长的字符串
> 使用Character类处理单个字符
> 从命令行传参数给main方法
> 使用File类获取文件属性、删除和重命名文件
> 使用PrintWriter类向文件写数据
> 使用Scanner类从文件读取数据
> 从Web上读取数据
### 字符串是不可变的
---

### 命令行传参数
---
- 参数个数
- 参数语义
- 在IJ中传入参数
![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405231027367.png)
### File类
---
使用文件类后需要关闭

`try-with-resources`
![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405231117128.png)

#### 读取方法
- `nextLine()`
	- 不跳过
	- 回车换行为止，同时**吸收（包括）回车换行**
	- 字符串，返回的字符串**不包含换行**
- `next() nextInt()...`令牌读取法
	- 先跳过空格
	- 以空格为止，不包括空格
	- 字符串$\rightarrow$格式
#### 替换文本
### 从web读取数据
---
