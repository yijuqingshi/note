# Js语法

## 基本语法
* 函数定义
```
function myFunction(name,age)
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

  基于事件的方式调用，例如onClick onsubmit等
```
  <form onsubmit="return myFunction()" action="session.jsp" >

  </form>
```

* 变量定义

  ```

  var a = "hello"; //成员变量

  function indexFormCommit() {

   var  b = "world";  //局部变量

   document.write(a + b);

   c = "hello world "; //成员变量
}
  ```
  定义在函数外的与不带var 的函数内的变量是成员变量，定义在函数内，带var定义的是局部变量

* html文件中引入js文件
  ```
  <script type="text/javascript" src="./../js/hello.js"></script>
  ```


* for in 语法

  ```
    //遍历object对象中的所有属性
    for(var property in object)
    {
         document.write( property + " = " + object[property])
    }
  ```  

## Js默认对象

* Date对象
  ```
   var date = new Date();
   date.getMonth();//年 月 日 周 时 分 秒
  ```

* Array对象

  使用方法：
  ```
  //可以是不同的元素
  var fruit = new Array("苹果","鸭梨"); //长度可变

  //第二种方式
  var fruit = ["苹果",10,"橘子"]

  //第三分钟
  var fruit = new Array();
  fruit.push("苹果");
  fruit.push("栗子");

  for(var i = 0; i < fruit.length;i++)
  {

  }

  ```
  常用方法
  ```
    var fruit = ["苹果",10,"橘子"];

    fruit.join("/"); 将数组元素以/符号分割
    输出结果为 苹果/10/橘子

    fruit.valueof(); //输出结果为 苹果，10，橘子

    fruit.toString(); //输出结果为 苹果，10，橘子

    fruit.reverse(); //反转元素

  ```

  二维数组

  使用方法
  ```
  var f = new Array(3);

  f[0] = [1,2];

  f.push(["aa","bb"]);

  f.push(["dd",10])
  ```
## 对象定义

  方式一
  ```
  function person(name,age) {
      this.name = name;
      this.age = age;
      //关联方法
      this.display = display;
  }

  function display() {

      //this代表调用的对象
       var str = this.name + ":" + this.age + "<br>";
       document.write(str);
       return str;
  }
  //方法调用
  yw.display();
  document.write(yw.name);
  document.write(yw.age);

  ```

* 定时器

  第一种方式
  ```
  function count()
  {
       //7秒后执行字符串中的js代码
       setTimeOut("alert('执行成功')",7000);
  }
  ```
  第二种方式
  ```
   //定时每隔1秒钟执行count()方法
   var timeID = setInterval("count()",1000);
   //停止执行count()
   clearInterval(timeID);
  ```


  * 绑定时间的两种方式

  第一种方式
  ```
    function getCount(){

    }

    <input type=button value = "click" onClick = getCount()>

  ```
  第二种方式
  ```
  var v = document.getElementById(button1);

  v.onClick = getCount; //注意此处不能写getCount();

  <input type=button value = "click" id = "button1">
  ```
