![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405091240070.png)

```java
//使用前先引入
import java.util.ArrayList;
```

```java
//创建一个空的列表
ArrayList<String> cityList = new ArrayList<>();
ArrayList<int> list = new ArrayList<>();//wrong
ArrayList<Integer> list1 = new ArrayList<>();//ok
```

```java
//从数组创建列表
String[] array = {"red", "green", "blue"};  
ArrayList<String> list = new ArrayList<>(Arrays.asList(array));
```

```java
//使用Array.asList()前先引入
import java.util.Arrays;
```


