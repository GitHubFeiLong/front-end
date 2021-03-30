# CSS 布局扩展

## Flex布局

​		CSS3 弹性盒子(Flexible Box 或 Flexbox)，是一种用于在页面上布置元素的布局模式，使得当页面布局必须适应不同的屏幕尺寸和不同的显示设备时，元素可预测地运行/列。对于许多应用程序，弹性盒子模型提供了对块模型的改进，因为它不使用浮动，flex容器的边缘也不会与其内容的边缘折叠。

弹性盒模型，分老版与新版
    老版本的我们通常称之为box
    新版本的我们通常称之为flex

容器与项目

主轴 与 侧轴
       由flex-direction/-webkit-box-orient确定

有了新版本后，为什么还需要老版本？（新版本比老版本要强大的很多）
    很多移动端浏览器内核版本都超低
       

### 老版

容器设置display为webkit-box

#### 容器的布局方向

```css
-webkit-box-orient: horizontal;
-webkit-box-orient: vertical;
```

> 注意:项目永远是在主轴上排列的
> -webkit-box-orient属性本质上确定了主轴是哪一根
> horizontal:x轴
> vertical:y轴

#### 容器的排列方向

```css
-webkit-box-direction: normal;
-webkit-box-direction: reverse;    
```

> 注意:项目永远是沿着主轴的正方向排列的
>  -webkit-box-direction属性本质上改变了主轴的方向

#### 富裕空间的管理

 富裕空间的管理（主轴）

​		  start
​          end
​          center
​          justify

```css
-webkit-box-pack:start; 不会给项目区分配空间，只是确定富裕空间的位置 
```

> 富裕空间的管理（侧轴）    
>
> ​		  start
> ​          end
> ​          center  
>
>  -webkit-box-align:center; 不会给项目区分配空间，只是确定富裕空间的位置

### 新版

容器设置display为flex

#### 容器的布局方向

```css
flex-direction: row;
flex-direction: column;
```





容器设置display为flex

## 新版Flex布局详解

## 响应式布局核心（媒体查询）

## 多列布局（分栏布局）