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

 * 方式一
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


  * 绑定事件的两种方式

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


## 内置对象

 * 使用说明
    ```
    window.history.back(-1)

    //跳转到此链接
    window.location.href = "wwww.baidu.com"

    document.links //获取页面所有链接对象，是数组

    document.cookie = "name=yangwei;expires=Wdy,DD-Mon-YY HH:MM:SS GMT    
    ```

## 理解函数

 * 在JavaScript中，函数function就是对象，没有方法重载的概念。

  ```
  function add(number){
    alert(number + 10);
  }
  等价于 var add = function(number){
    alert(number + 10);
  }

  function add(number, number1){
    alert(number + number1);
  }
  等价于 var add = function(number,number1){
    alert(number + number1);
  }
  ```

* 在JavaScript中有一个Function对象，所有自定义的函数都是Function类型的对象。  Function对象接受的参数都是字符串类型的，最后一个参数是函数需要执行的方法体，其他的参数是函数接受的真正参数。例如：
```
 var add = new Function("number","number1","alert(number + number1)")
 //调用
 add(10,20);
```  
* 在JavaScript中,函数中隐含一个arguments数组对象，表示调用该函数传进来的实际的参数。例如：
  ```
  add(10,20,30);

  则相当于
  add(number,number1){
    arguments[0] = 10;
    arguments[1] = 20;
    arguments[2] = 30; //与number,number1无关。
  }
  ```
