# 1. Flex布局

布局的传统解决方案，基于[盒状模型](https://developer.mozilla.org/en-US/docs/Web/CSS/box_model)，依赖 [`display`](https://developer.mozilla.org/en-US/docs/Web/CSS/display) 属性 + [`position`](https://developer.mozilla.org/en-US/docs/Web/CSS/position)属性 + [`float`](https://developer.mozilla.org/en-US/docs/Web/CSS/float)属性。它对于那些特殊布局非常不方便，比如，[垂直居中](https://css-tricks.com/centering-css-complete-guide/)就不容易实现。

------

`

### 1.1 什么是flex布局以及flex布局又什么作用 

```html
 什么是flex :    flex是Flexible box 的缩写 意为弹性布局 它可以为传统的盒子布局提供最大的灵活性并且任何东西都是可以设置的   
flex有什么作用 :  填补了浮动托标的缺点 
```

### 1.2flex初体验

一般想做到这种的模板 都是用浮动 float:left 但是浮动有个缺点就是容易托标

![image-20210430151935691](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210430151935691.png)

![image-20210430152206667](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210430152206667.png)

这样很麻烦而且有时候还得给父盒子添加overflow:hidden;

flex定位来了

![image-20210430152331426](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210430152331426.png)

只需要简单一行代码就可以完成

### 1.3

主轴和方向

主轴默认是水平方向 侧轴默认是垂直方向

修改主轴方向属性: flex-diretion



|     属性值     |      作用       |
| :------------: | :-------------: |
|   row(默认)    | 行,水平(默认值) |
|     column     |     列,垂直     |
|  row-reverse   |   行,从右往左   |
| column-reverse |   列,从下到上   |



![image-20210430153748760](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210430153748760.png)

默认是这样的 

跟改了flex-direction:column;之后 就变成了这样

![image-20210430153843215](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210430153843215.png)

### 1.4对齐方式

1. 主轴对其方式 

    1.1修改主轴对齐方式属性 : justify-content:

   - 属性值 

   |    属性值     |                        作用                        |
   | :-----------: | :------------------------------------------------: |
   |  flex-start   |              默认值.起点开始依次排列               |
   |   flex-end    |                  终点开始依次排列                  |
   |    center     |                   沿主轴剧中排列                   |
   | space-around  | 弹性盒子沿主轴均匀排列, 空白间距均分在弹性盒子两侧 |
   | space-between | 弹性盒子沿主轴均匀排列, 空白间距均分在相邻盒子之间 |
   | space-evenly  | 弹性盒子沿主轴均匀排列, 弹性盒子与容器之间间距相等 |

   1.2修改侧轴对齐方式属性align-items

   - 属性值

      

     |          属性值          |                   作用                    |
     | :----------------------: | :---------------------------------------: |
     |        flex-start        |          默认值,起点开始依次排列          |
     |         flex-end         |             终点开始依次排列              |
     |          center          |              沿侧轴剧中排列               |
     |         stretch          | 默认值,弹性盒子沿着主轴线被拉伸至铺满容器 |
     | align-self(设置给子元素) |      可以单独控制其在侧轴的对其方式       |

     

align-self是设置给单独元素的值和justify-content的值一样



#### flex换行 

flex-wrap属性 有三个值	 

|      nowrap      |                          默认不换行                          |
| :--------------: | :----------------------------------------------------------: |
|     **wrap**     | **当flex项目总宽度大于flex容器的宽度的时候就会换行(一般都是压缩项目)** |
| **wrap-reverse** |               **换行并且第一行和二行交换位置**               |



组合写法 

flex-flow 

flex-flow 属性是flex-direction 和 flex-wrap属性简写方式 默认值为 row nowrap

flex-flow:row nowrap  下次有这两个属性的时候直接用	flex-flow就行 属性值就是本来的属性值







#### align-content属性 

align-content属性定义了多根轴向的对齐方式.如果项目只有一根轴向该属性不起作用

align-content 属性值 和justify-content是一样的 

![image-20210506144911431](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210506144911431.png)

## 项目的属性

1. order

2. flex-show

3. flex-shrink

4. flex-basis

5. flex 

   #### 1.1order属性

   order属性定义项目的排列顺序 数值越小排列越靠前默认值为0

   ![image-20210506145232658](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210506145232658.png)



#### 2.flex-grow属性 

flex-gorw属性定义项目的放大比列默认值为0![image-20210506145353321](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210506145353321.png)



#### 3.flex-shrink属性

flex-shrink属性定义了项目的缩小比列![image-20210506150009909](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210506150009909.png)

效果

![image-20210506150026753](C:\Users\徐培栋\AppData\Roaming\Typora\typora-user-images\image-20210506150026753.png)



#### flex-basis属性

flex-basis属性定义了属性定义了在分配多余空间之前,项目占据的主轴空间（main size）.浏览器根据这个属性,计算主轴是否有多余空间.它的默认值为`auto`,即项目的本来大小.

#### flex属性

flex属性是flex-grow,flex-shrink,flexbasis的简写

flex:<flex-grow><flex-shrink><flexshrink>

