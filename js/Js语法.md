# Js语法

* 函数定义
```
function myFunction()
   {
       alert("Hello World!");

       return false;
   }
```

* 获取元素
```
var username = document.getElementById("username")<br>
var elements = document.getElementsByName("username")<br>
```

* 函数的调用
<br>
基于事件的方式调用，例如onClick onsubmit等
```
  <form onsubmit="return myFunction()" action="session.jsp" >

  </form>
```
