```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
        "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
    <meta http-equiv="Content-Type"  content="text/html" charset="UTF-8">
    <title>这是网页标题</title>

    //引入CSS文件
    <link  rel="stylesheet" type="text/css" href="../css/index.css">
    //定义CSS样式
    <style type="text/css">

        .center {text-align: center;color: red}

    </style>
     //引入JS文件
    <script type="text/javascript" src="./../js/hello.js"></script>
    //定义JS脚本
    <script type="text/javascript">

                function test() {
                    document.write("hello world")
                }
    </script>
</head>
<body>
      <h1 class="center"><font color="red">这是一个标题1</font></h1>

      <p class="center">这是一个段落</p>
      <p class="rigth" style="color: red;text-align: center">这是一个段落</p>

      <a href= login.html>登录</a>

      <br>

      <form>
           username:<input type="text"><br>
           password:<input type="password"><br>
           兴趣：游泳<input type="checkbox">  睡觉<input type="checkbox"><br>
           性别：男<input type="radio" name="grand">
           性别：女<input type="radio" name="grand"><br>
           学历：<select>
                 <option>小学</option>
                 <option>初中</option>
                 <option>高中</option>
                 <option>大学</option>
                </select><br>
           评论：<textarea >

                </textarea><br>
           上传文件：<input type="file"><br>
           图片：<img src="../images/1011076-20170215220735519-338241964.png" width="10%" height="10%"><br>
          <input type="submit" value="submit">&nbsp;&nbsp;<input type="reset" value="reset">
          <input type="button" value="button" onclick="javascript:alert(true);">
      </form>


</body>
</html>

```
