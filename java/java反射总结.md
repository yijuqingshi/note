# Java反射总结

#### 一、获取Class对象的三种方式
1. Class.formName("包名.类名")
2. Object.Class
3. mObject.getClass();

注意：创建此类对象的两种方式
1. class.newInstance();
2. 获取对应的构造方法对象，执行newInstance方式

#### 二、获取方法对象

1. class.getMetheds() //获取所有public方法
2. class.getMethed(方法名,参数的class对象);//获取指定的public方法
3. class.getDeclaredMethods()//获取私有的所有的方法
4. class.getDeclaredMethod(方法名，参数Class对象)//获取对应的私有方法


* 注意：执行method.invoke方法时私有方法得调用method.setAccessible(true)授权

####  三、获取属性

1. class.getDeclaredFields()//获取此类的所有的属性对象
2. class.getDeclaredField("name") //获取指定的属性对象

#### 四、获取构造方法

1. class.getConstructors()//获取所有的构造方法
2. class.getConstructor(class对象)获取构造方法对象

#### 五、获取元素注解

1. class/methed/field.getAnnotations() //获取此元素对象上的所有注解

2. class/methed/field.getAnnotation(MyAnnotation.clsss) //获取MyAnnotation实例

3. class/methed/field.isAnnotationPresent(MyAnnotation.clsss);//判断MyAnnotation注解是否有修饰此元素


####  六、Junit4的执行流程

* 获取测试类的class对象，通过class对象获取该类的method数组
2. 遍历method数组，获取每一个method对象，执行method.isAnnotationPresent(Test.class)方法，判断该方法是否被Test注解修饰。
3. 如果是被Test注解修饰，那么执行该method.invoke方式，执行，否则不
