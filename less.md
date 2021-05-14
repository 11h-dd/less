# less

### 概览

1. **less(leaner Style Sheets的缩写)是一门向后兼容的css扩展语言是css预处理器,它扩展css语言,增加了变量,函数等等使css更加容易维护和扩展less可以运行在Node或者浏览器端**
2. **后缀名为.less**



### less初体验

我们做一个这样的效果

### ![image-20210510143822568](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510143822568.png)		

html代码 

```html
<div class="father">
    <div class="son"></div>
</div>
```



传统的css代码

![image-20210510143944492](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510143944492.png)	

会发现代码中有好多都是一样的而且如果不设置father son这样的类名可能就不知道那个是父盒子那个是子盒子了

这个就是传统css写发的问题

下面用less来看一下

![image-20210510144125504](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510144125504.png)	

我们将一样的代码放到.center中 想要用的话直接.center这样就可以了 而且这样结构更加清晰了 知道谁知父盒子谁是子盒子

但是因为less代码无法被浏览器识别,实际开发需要转化成css使用link标签引入css文件 

我们就需要一个vscode插件 这个插件可以将less自动转化成css文件(只要less一保存 里一个css文件也会一起保存的)

![image-20210510144705989](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510144705989.png)	

less嵌套规则 

![image-20210510154605040](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510154605040.png)	

在less嵌套需要这样

![image-20210510154633003](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510154633003.png) 

编译成css 是这样的  这就是less好处 层次分明

![image-20210510154652117](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510154652117.png)	





less扩展 : ~ 转义符

![image-20210510154312297](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510154312297.png)

但是我门加了 '~' 转义符之后就可以了

![image-20210510154455690](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510154455690.png) 

less会延迟加载

![image-20210510202008814](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510202008814.png)	



这个两个答案是什么  three按一般逻辑来说是2   one是1

下面看答案

![image-20210510202121334](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510202121334.png)	

为什么three是3呢  **在less里面变量会延迟加载 他是会都读完才会写结果three最后一个是@var是3 所以three是3 这是less里面(需要记住的东西)less会等到所有的都运行完了才做结果 -- > 变量的延迟加载	**

### 正式开始学习less

#### 1.less变量 

- 什么是变量 :  和js中变量是一样的 保存数据的容器
- less中定义变量的格式 :  @变量名称 : 值      例子 --->    @w:width;(这就是把width保存到了@w中以后用width就直接用@w就可以了)
- less使用变量的格式 :  @变量名称:
- 变量赋值 : @变量名称 : @变量名称;
- 定义在{}里面就是局部变量  定义在{}外面就是全局变量 (和js一样)

  ![image-20210510145541875](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510145541875.png)	

这样自动生成的css是这样的

![image-20210510145609417](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510145609417.png)	

#### less中的注释

1. 同js注释,分单行注释和多行注释(同js一样)
2. 区别:是否被编译     {1. 单行注释不会被编译(不会出现在编译后的文件中)  2. 多行注释会被编译 (会出现在编译后的文件中)}

这是less文件

![image-20210510145915085](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510145915085.png)	

这个是被编译后的 只有多行注释才会被编译后的文件展示出来

![image-20210510145927501](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510145927501.png)	

#### less语法 -- 插值

1. 什么是插值 : 属性名称或者选择器名称并可以使用变量
2. 变量插值的格式 : @{变量名称}

插值就是那些属性 width height background-color border .........

![image-20210510150141058](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510150141058.png)	

插值记住语法就行 

#### less运算

html格式

![image-20210510143924558](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510143924558.png)	

**支持+-*/**

![image-20210510150556601](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510150556601.png)	

效果是一样的

![	](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510150648439.png)	

#### less语法混合

什么是less中的混合(Mix in)

1. 将需要重复使用的代码封装到一个类中,在需要使用的地方调用封装好的类即可
2. 在预处理的收less会自动将用到封装好的类中的代码拷贝过来

本质就是 赋值 --> 粘贴

普通混合 : 缺点会将多余的代码弄到css里面去

  **less中混合的注意点 **

1. **如果混合名称的后面没有(), 那么在预处理的时候, 会保留混合的代码**
2. **如果混合名称的后面加上(), 那么在预处理的时候, 不会保留混合的代码**



![image-20210510151507805](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510151507805.png)	



这时候就需要混合了我们只需要加一个括号就好了(就和js的函数一样封装好以后哪里需要用调用就行)

![image-20210510151620164](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510151620164.png)	

#### less语法 -- 带参数的混合和默认值混合 还有 内置方法

本质:就和js函数里面的传参一样

![image-20210510151747916](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510151747916.png)

![image-20210510151809900](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510151809900.png)	

​				![image-20210510205143871](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510205143871.png)

这样就可以







#### less嵌套规则(&)

![image-20210510202702032](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510202702032.png)	

![image-20210510202720098](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510202720098.png)	

这是一般的less嵌套的方式可是如果要在.inner后面弄一个:hover要咋办呢 肯定是有想直接在里面写:hover的

![image-20210510202821792](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510202821792.png)	

可以css解析成这样的

![image-20210510202959533](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510202959533.png)									

这样是不对的不会起作用的 (这样的话就算是.inner和:hover是父子关系了 要想让他门是平级关系咋办呢)

![image-20210510203133718](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510203133718.png)		

![image-20210510203157659](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210510203157659.png)	

灭空格里(&就代表自身的父元素)

#### less继承(:extend(需要继承的混合))

> 继承的语法 : div:extend(混合){}

**注意继承的混合不能假括号**

一般的混合是这样的

![image-20210513195451990](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210513195451990.png)

但是继承确是这样的 这个就是继承的好处

![image-20210513195540107](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210513195540107.png)

#### less中的函数 

记住一些就行![image-20210513195715094](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210513195715094.png)

#### less中的循环判断

用when来做关键字

![image-20210513200036659](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210513200036659.png)

合并属性![image-20210513200328039](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210513200328039.png)

less完结