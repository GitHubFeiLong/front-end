# CSS 过渡 & 变形

## 过渡

> 过渡只关心元素的初始状态和结束状态，没有方法可以获取元素在过渡中每一帧的状态
>
> 元素在初次渲染还没有结束的时候，是没有办法触发过渡的
>
> 在绝大部分变换样式的切换时，变换组合的个数或位置不一样时，是没有办法触发过渡的

### transition  

   	 众所周知，css效率极高，其变化的过程往往都是在一瞬间完成，速度极快。
    	CSS transition 提供了一种在更改CSS属性时控制动画速度的方法。 其可以让属性变化成为一个持续一段时间的过程，而不是立即生效的。比如，将一个元素的颜色从白色改为黑色，通常这个改变是立即生效的，使用 CSS transitions 后该元素的颜色将逐渐从白色变为黑色，按照一定的曲线速率变化。这个过程可以自定义

+ 简写属性transition:
  transition是一个简写属性，用于 

  + transition-property
  + transition-duration
  + transition-timing-function
  + transition-delay。 

  > CSS 过渡 由简写属性 transition 定义是最好的方式，可以避免属性值列表长度不一，节省调试时间 

+ 默认值：
      transition-delay: 0s
      transition-duration: 0s
      transition-property: all
      transition-timing-function: ease

> 注意:
> 在transition属性中，各个值的书写顺序是很重要的：第一个可以解析为时间的值会被赋值给transition-duration，第二个可以解析为时间的值会被赋值给transition-delay
>
> 推荐抒写顺序:
>  过渡时间  过渡样式  过渡形式  延迟时间 [，过渡时间  过渡样式  过渡形式  延迟时间]
>
> 兼容性
>  transition 可以不用厂商前缀，不过鉴于标准刚刚稳定，对于基于 Webkit的浏览器仍然需要厂商前缀。如果想兼容旧版本的浏览器那么也需要厂商前缀（例如Firefox 15 及之前版本, Opera 12 及之前版本)
>
> 当属性值的列表长度不一致时:
> 跟时间有关的重复列表
> transition-timing-function使用默认值

#### transition-property

指定应用过渡属性的名称，默认值为 all，表示所有可被动画的属性都表现出过渡动画(https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_animated_properties)

可以指定多个 property 

属性值：  

+ none 没有过渡动画。
+ all 所有可被动画的属性都表现出过渡动画。
+ IDENT 属性名称 （可以指定多个）

> 指定过渡动画的属性（并不是所有的属性都可以动画）

#### transition-duration

​		属性以秒或毫秒为单位指定过渡动画所需的时间。
默认值为 0s ，表示不出现过渡动画。

可以指定多个时长，每个时长会被应用到由 transition-property 指定的对应属性上。如果指定的时长个数小于属性个数，那么**时长列表会重复**。如果时长列表更长，那么该列表会被裁减。两种情况下，属性列表都保持不变。

属性值

+ 以毫秒或秒为单位的数值

  > `<time>` 类型。表示过渡属性从旧的值转变到新的值所需要的时间。如果时长是 0s ，表示不会呈现过渡动画，属性会瞬间完成转变。不接受负值。一定要加单位(不能写0 一定要写0s  1s,0s,1s)！

> 指定过渡动画的时间（0也要带单位）

#### transition-timing-function

​		CSS属性受到 transition的影响，会产生不断变化的中间值，而 CSS transition-timing-function 属性用来描述这个中间值是怎样计算的。实质上，通过这个函数会建立一条加速度曲线，因此在整个transition变化过程中，变化速度可以不断改变
默认值：ease

你可以规定多个timing function,通过使用 transition-property属性，可以根据主列表(transition property的列表)给每个CSS属性应用相应的timing function.如果timing function的个数比主列表中数量少，缺少的值被设置为初始值（ease） 。如果timing function比主列表要多，timing function函数列表会被截断至合适的大小。这两种情况下声明的CSS属性都是有效的。

属性值：
         1、ease：（加速然后减速）默认值，ease函数等同于贝塞尔曲线(0.25, 0.1, 0.25, 1.0).
         2、linear：（匀速），linear 函数等同于贝塞尔曲线(0.0, 0.0, 1.0, 1.0).
         3、ease-in：(加速)，ease-in 函数等同于贝塞尔曲线(0.42, 0, 1.0, 1.0).
         4、ease-out：（减速），ease-out 函数等同于贝塞尔曲线(0, 0, 0.58, 1.0).
         5、ease-in-out：（加速然后减速），ease-in-out 函数等同于贝塞尔曲线(0.42, 0, 0.58, 1.0)
         6、cubic-bezier： 贝塞尔曲线
         7、step-start：等同于steps(1,start)
         8、step-end：等同于steps(1,end)
         9、steps(`<integer>`,[,[start|end]]?)
                      第一个参数：必须为正整数，指定函数的步数
                      第二个参数：指定每一步的值发生变化的时间点（默认值end）

> 指定过渡动画的形式（贝塞尔）

#### transition-delay

> 指定过渡动画的延迟

​		transition-delay属性规定了在过渡效果开始作用之前需要等待的时间。
默认值：0s 

​		你可以指定多个延迟时间，每个延迟将会分别作用于你所指定的相符合的css属性。如果指定的时长个数小于属性个数，那么时长列表会重复。如果时长列表更长，那么该列表会被裁减。两种情况下，属性列表都保持不变

属性值
       值以秒（s）或毫秒（ms）为单位，表明动画过渡效果将在何时开始。取值为正时会延迟一段时间来响应过渡效果；取值为负时会导致过渡立即开始。

#### 属性值的列表长度不一致时

```css
transition-property: background,width,height;
transition-duration: 3s,2s;
transition-delay:3s,2s;
transition-timing-function:linear;
```

```css
transition-property: background,width,height;
transition-duration: 3s,2s,3s;
transition-delay:3s,2s,3s;
transition-timing-function:linear,ease,ease;
```

> 超出的情况下是会被全部截掉的
>
> 不够的时候，关于时间的会重复列表，
>
> transition-timing-function的时候使用的是默认值ease

 

#### 检测过渡是否完成

​		当过渡完成时触发一个事件，在符合标准的浏览器下，这个事件是 transitionend, 在 WebKit 下是 webkitTransitionEnd
（每一个拥有过渡的属性在其完成过渡时都会触发一次transitionend事件）

> 在transition完成前设置 display: none，事件同样不会被触发

 ```javascript
dom.addEventListener("transitionend",function(){
    alert("end");
})
 ```

> transtionend事件（DOM2）在每个属性完成过渡时都会触发这个事件

## 变形

> 顺序是从右往左的，变换的底层其实就是矩阵的运算

### 2D变形transform

transform 属性允许你修改CSS视觉格式模型的坐标空间
transform 属性 , 只对 block 级元素生效！

#### 旋转（rotate）

```css
transform:rotate(angle); 
```

angle 为正值时:顺时针旋转  rotate(360deg)
angle 为负值:逆时针旋转  rotate(-360deg)

> 只能设单值。正数表示顺时针旋转，负数表示逆时针旋转

#### 平移（translate）

+ X方向平移:transform:  translateX(tx)
+ Y方向平移:transform:  translateY(ty) 
+ 二维平移：transform:  translate(tx[, ty])； 如果ty没有指定，它的值默认为0。

> 可设单值，也可设双值。
> 正数表示XY轴正向位移，负数为反向位移。设单值表示只X轴位移，Y轴坐标不变。
> 例如:
>
> ```css
> transform: translate(100px);
> ```
>
> 等价于
>
> ```css
> transform: translate(100px,0);
> ```

#### 倾斜（skew）

```css
transform:skewX(45deg);
```

+ X方向倾斜:transform:  skewX(angle)

  > skewX(45deg):参数值以deg为单位 代表与y轴之间的角度

+ Y方向倾斜:transform:  skewY(angle)

  >skewY(45deg):参数值以deg为单位 代表与x轴之间的角度

+ 二维倾斜:transform:  skew(ax[, ay]);  如果ay未提供，在Y轴上没有倾斜

  > skew(45deg,15deg):参数值以deg为单位 第一个参数代表与y轴之间的角度,第二个参数代表与x轴之间的角度。单值时表示只X轴扭曲，Y轴不变，如
  >
  >```css
  >transform: skew(30deg);
  >等价于                     
  >transform: skew(30deg, 0);
  >```
  >
  >考虑到可读性，不推荐用单值，应该用
  >
  >```css
  >transform: skewX(30deg);
  >```
  >
  >skewY表示  只Y轴扭曲，X轴不变。 

> 正值:拉正斜杠方向的两个角
> 负值:拉反斜杠方向的两个角                   

#### 缩放（scale）

```css
transform:scale(2);
```

+ X方向缩放:transform:  scaleX(sx); 

+ Y方向缩放:transform:  scaleY(sy);

+ 二维缩放 :transform:  scale(sx[, sy]);  (如果sy 未指定，默认认为和sx的值相同)  

  > 要缩小请设0.01～0.99之间的值，要放大请设超过1的值。
  >
  > 例如缩小一倍可以
  >
  > ```css
  > transform: scale(.5);
  > ```
  >
  > 放大一倍可以：
  >
  > ```css
  > transform: scale(2);
  > ```
  >
  > 如果只想X轴缩放，可以用scaleX(.5)相当于scale(.5, 1)。 同理,只想Y轴缩放，可以用scaleY(.5)相当于scale(1, .5)

> 注意：
>
> 正值:缩放的程度
> 负值:不推荐使用（有旋转效果）
> 单值时表示只X轴,Y轴上缩放粒度一样，如transform: scale(2);等价于transform: scale(2,2);

#### 基点的变换

放在需要改变基点的元素身上：

```css
transform-origin: 100px 100px;
```

> 从元素的左上角值是 0，0；往右x增加，往下y增加

 transform-origin CSS属性让你更改一个元素变形的基点。

#### 矩阵（matrix）

在 2D变换 中，矩阵变换函数 matrix() 接受 6个值，语法形式如下：
       transform: matrix(a, b, c, d, e, f);  

这相当于，对元素应用一个如下的变换矩阵：

![image-20210329173921872](CSS 过度&变形.assets/image-20210329173921872.png)

点(Xi,Yi,1)进行变换后的新坐标

![image-20210329173937311](CSS 过度&变形.assets/image-20210329173937311.png)

即根据变换矩阵进行变换之后点 (xi,yi) 的坐标是(axi+cyi+e,bxi+dyi+f)

##### 旋转

对某一元素应用旋转变换 rotate(θ)，相当于对其应用如下变换矩阵：

![image-20210329174029991](CSS 过度&变形.assets/image-20210329174029991.png)

即等价于矩阵变换函数 matrix(cosθ, sinθ, -sinθ, cosθ, 0, 0)。

##### 平移

对某一元素应用旋转变换 translate(X, Y)，相当于对其应用如下变换矩阵：

![image-20210329174049226](CSS 过度&变形.assets/image-20210329174049226.png)

即等价于使用矩阵变换函数 matrix(1, 0, 0, 1, X, Y)。

##### 倾斜

对某一元素应用倾斜变换 skew(α, β)，相当于对其应用如下变换矩阵：

![image-20210329174108071](CSS 过度&变形.assets/image-20210329174108071.png)

即等价于使用矩阵变换函数 matrix(1, tanβ, tanα,1, 0, 0)。

##### 缩放

对某一元素应用缩放变换 scale(scaleX, scaleY)，相当于对其应用如下变换矩阵：

![image-20210329174129839](CSS 过度&变形.assets/image-20210329174129839.png)

即等价于使用矩阵变换函数 matrix(scaleX, 0, 0, scaleY, 0, 0)

### 3D变形

在浏览器中，X轴是从左到右，Y轴是从上到下，Z轴是从里到外

![image-20210329174338400](CSS 过度&变形.assets/image-20210329174338400.png)