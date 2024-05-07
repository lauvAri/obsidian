使用`appendChild`，把一个子节点添加到父节点的最后一个子节点。例如：

```
<!-- HTML结构 -->
<p id="js">JavaScript</p>
<div id="list">
    <p id="java">Java</p>
    <p id="python">Python</p>
    <p id="scheme">Scheme</p>
</div>
```

把`<p id="js">JavaScript</p>`添加到`<div id="list">`的最后一项：

```
var
    js = document.getElementById('js'),
    list = document.getElementById('list');
list.appendChild(js);
```

现在，HTML结构变成了这样：

```
<!-- HTML结构 -->
<div id="list">
    <p id="java">Java</p>
    <p id="python">Python</p>
    <p id="scheme">Scheme</p>
    <p id="js">JavaScript</p>
</div>
```

因为我们插入的`js`节点已经存在于当前的文档树，因此这个节点首先会从原先的位置删除，再插入到新的位置。

更多的时候我们会从零创建一个新的节点，然后插入到指定位置：
```
 <div id="list">
        <p id="java">Java</p>
        <p id="python">Python</p>
        <p id="scheme">Scheme</p>
        <p id="js">JavaScript</p>
    </div>
    <script>
        var list = document.getElementById('list');
        var haskell = document.createElement("p");
        haskell.id = "haskell";
        haskell.innerText = "Haskell";
        list.appendChild(haskell);//添加了一个新的结点
    </script>
```

## `insertBefore`

```
   <script>
        var list = document.getElementById('list');
        var ref = document.getElementById('python');
        var haskell = document.createElement('p');
        haskell.id = 'haskell';
        haskell.innerText = 'Haskell';
        list.insertBefore(haskell, ref);//将haskell插入到python前面
    </script>
```

很多时候，需要循环一个父节点的所有子节点，可以通过迭代`children`属性实现：

```
var
    i, c,
    list = document.getElementById('list');
for (i = 0; i < list.children.length; i++) {
    c = list.children[i]; // 拿到第i个子节点
}
```
