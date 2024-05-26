
> [!abstract] 
> 从命令行传参数给main方法
> 使用File类获取文件属性、删除和重命名文件
> 使用PrintWriter类向文件写数据
> 使用Scanner类从文件读取数据
> 从Web上读取数据

### 命令行传参数
---
- 参数个数
- 参数语义
- 在IJ中传入参数
![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405231027367.png)
### File类
---
```java
java.io.File file = new java.io.File("文件路径.png");
        //File 对象代表的文件和目录存在 boolean
        System.out.println("Does it exist? " + file.exists());
        //返回文件大小，如果不存在或者是一个目录的话返回0 long
        System.out.println("The file has " + file.length() + " bytes");
        //File 对象代表的文件存在且可读 boolean
        System.out.println("Can it be read? " + file.canRead());
        //File 对象代表的文件存在且可写 boolean
        System.out.println("Can it be written? " + file.canWrite());
        //File 对象代表的是一个目录 boolean
        System.out.println("Is it a directory? " + file.isDirectory());
        //File 对象代表的是一个文件 boolean
        System.out.println("Is it a file? " + file.isFile());
        //File 对象是采用绝对路径名创建 boolean
        System.out.println("Is it absolute? " + file.isAbsolute());
        //File 对象代表的文件是隐藏的 boolean
        System.out.println("Is it hidden? " + file.isHidden());
        //返回 File 对象代表的文件和目录的完整绝对路径名
        System.out.println("Absolute path is " +
                file.getAbsolutePath());
        System.out.println("Last modified on " +
                new java.util.Date(file.lastModified()));
```
### 文件输入和输出
---
- 创建文件的时机
- 使用文件类后需要关闭
```java
package Java语言程序设计基础.文件输入和输出;

import java.io.FileNotFoundException;
import java.io.PrintWriter;

public class WriteDate {
    public static void main(String[] args) throws FileNotFoundException {
        java.io.File file = new java.io.File("scores.txt");

        //检查文件是否存在，若存在，则退出此程序
        if(file.exists()){
            System.out.println("File already exists");
            System.exit(1);
        }

        //create a file
        //创建PrintWriter对象时，才会产生文件
        PrintWriter out = new PrintWriter(file);

        //write formatted output to the file
        out.print("John T Smith ");
        out.println(90);
        out.print("Eric K Jones ");
        out.println(85);

        //close the file
        //必须调用此方法，否则数据不能正确地保存在文件中
        out.close();


    }

}

```

- `try-with-resources`，这样可以不用手动关闭
![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405231117128.png)
```java
package Java语言程序设计基础.文件输入和输出;

import java.io.FileNotFoundException;

public class WriteDataWithAutoClose {
    public static void main(String[] args) throws FileNotFoundException {
        java.io.File file = new java.io.File("score.txt");
        if(file.exists()){
            System.out.println("File already exists");
            System.exit(0);
        }

        try(
                //声明和创建资源
                java.io.PrintWriter out = new java.io.PrintWriter(file);
                ){
            //write formatted output to the file
            out.print("John T Smith ");
            out.println(90);
            out.print("Eric K Jones ");
            out.println(85);
        }
    }
}

```
#### 读取方法
- `nextLine()`
	- 不跳过
	- 回车换行为止，同时**吸收（包括）回车换行**
	- 字符串，返回的字符串**不包含换行**
- `next() nextInt()...`令牌读取法 token-reading method
	- 先跳过空格
	- 以空格为止，不包括空格
	- 字符串$\rightarrow$格式
>路径：在 IJ 中路径是基于content root，即项目文件夹
```java
File file = new File("src/Java语言程序设计基础/文件输入和输出/ReadData.java");
        Scanner in = new Scanner(file);
        while(in.hasNext()){
            System.out.println(in.nextLine());
        }
        in.close();
```

#### 替换文本

```java
package Java语言程序设计基础.文件输入和输出;
import java.io.*;
import java.util.*;

public class ReplaceText {
    public static void main(String[] args) throws Exception {
        // Check command line parameter usage
        if (args.length != 4) {
            System.out.println(
                    "Usage: java ReplaceText sourceFile targetFile oldStr newStr");
            System.exit(0);
        }

        // Check if source file exists
        File sourceFile = new File(args[0]);
        if (!sourceFile.exists()) {
            System.out.println("Source file " + args[0] + " does not exist");
            System.exit(0);
        }

        // Check if target file exists
        File targetFile = new File(args[1]);
        if (targetFile.exists()) {
            System.out.println("Target file " + args[1] + " already exists");
            System.exit(0);
        }

        // Create input and output files
        Scanner input = new Scanner(sourceFile);
        PrintWriter output = new PrintWriter(targetFile);

        while (input.hasNext()) {
            String s1 = input.nextLine();
            String s2 = s1.replaceAll(args[2], args[3]);
            output.println(s2);
        }

        input.close();
        output.close();
    }
}

```

IJ 的运行配置如下：

![image.png](https://obsidian-1326430649.cos.ap-chongqing.myqcloud.com/pic/202405250932577.png)
```
程序执行的效果是将ReadData.java中的 "Scanner" 全部替换成 "Scan" 并保存在doc文件夹下的 "record.txt" 中
```
### 从web读取数据
---
