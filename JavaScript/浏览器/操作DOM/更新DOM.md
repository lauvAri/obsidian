```
<div id="test-div">
        <p id="test-js">javascript</p>
        <p>Java</p>
      </div>
      <script>
        var js = document.getElementById("test-js");
        js.innerHTML = "JavaScript";
        js.style.color= "#ff0000";
        js.style.fontWeight = "bold";//注意在css中写法为font-weight, 但在js中我们应该使用驼峰命名法
      </script>
```


