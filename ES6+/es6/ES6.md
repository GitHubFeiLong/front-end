# ES 

## ES6

### let

+  变量不能重复声明

```javascript
let a;
let b,c,d;
let f= 521, g = 'iloveyou', h = [];
// 报错 (Uncaught SyntaxError: Identifier 'star' has already been declared)
let star = '罗志祥';
let star = '罗志祥';
```

+ 块级作用域(还有 全局作用域，函数作用域， eval作用域）

```javascript
// var
{
    var girl = '周扬青';
}
	console.log(girl); // '周扬青'
// let
{
    let girl = '周扬青';
}
	console.log(girl); // girl is not defined
```

+ 不存在变量提升

  ```javascript
  console.log(song); // undefined
  var song = '恋爱达人';
  console.log(song1); // Cannot access 'song1' before initialization
  let song1 = '恋爱达人';
  ```

+ 不影响作用域链

  ```javascript
  {
      let school = '尚硅谷';
      function fn () {
      	console.log(school); //尚硅谷
      }
      // fn没有变量，会往上层找该变量
   	fn();
  }
  ```

> 使用循环时
>
> 如果使用 var 因为i没有块级作用域，循环结束后，i自增变为了3
>
> ```javascript
> for(var i = 0; i < 3; i++){}
> console.log(window.i); // 3
> ```

### const 声明常量

+ 一定要赋初始值
+ 一般常量使用大写
+ 常量的值不能修改
+ 块级作用域(跟let类似)
+ 对于数组和对象的元素修改，不算对常量的修改，不会报错。

### 变量解构赋值

允许按照一定模式从数组和对象中提取值，对变量进行赋值，这被称为解构赋值

+ 数组的解构

  ```javascript
  const F4 = ['小沈阳', '刘能', '赵四', '宋小宝'];
  let [xiao, liu, zhao, song] = F4;
  console.log(xiao, liu, zhao, song);// 小沈阳 刘能 赵四 宋小宝
  ```

+ 对象的解构

  ```javascript
  const zhao = {
      name : '赵本山',
      age: '不详',
      xiaoping:  function () {
          console.log("我可以");
      }
  }
  
  let {name, age, xiaoping} = zhao;
  console.log(name, age, xiaoping);
  xiaoping()
  ```

  > 注意，变量和属性名称一致，不然结果是undefined

### 模板字符串

ES6 引入新的声明字符串的方式 [``]

+ 声明

  ```javascript
  let str = `我也是一个字符串`;
  console.log(str, typeof str)//我也是一个字符串 string
  ```

+ 内容中可以直接出线换行符

  ```javascript
  let str = `<ul>
                  <li></li>
              </ul>`
  ```

+ 变量拼接

  ```javascript
  let name = '沈腾';
  let str = `${name}是我心目中最搞笑的演员！`; 
  console.log(str); // 沈腾是我心目中最搞笑的演员！
  ```

### 简化对象写法

ES6 允许再大括号里面，直接写入变量和函数，作为对象的属性和方法，这样的书写更加简洁

```javascript
let name = '尚硅谷';
let change = function () {
    console.log('我们可以改变你！！');
}
// 原来
const SCHOOL = {
    name:name,
    change:change,
    // 方法
    myMethod: function (){
        console.log('我是自定义方法！！');
    }
}
// 现在
const SCHOOL = {
    name,
    change,
    myMethod(){
        console.log('我是自定义方法！！');
    }
}
```



### 箭头函数

ES6 允许使用 箭头（=>） 定义函数

+ this是静态的，this始终指向**函数声明时**所在作用域下的this值
+ 不能作为构造实例化对象
+ 不能使用 arguments 变量
  + 省略小括号，当形参有且只有一个的时候
  + 省略花括号，当代码只有一条语句的时候,return 必须省略，而且语句的执行结果就是函数的返回值
+ 箭头函数的简写

> call 方法调用 (可以更改函数内部this的值)，格式： 方法.call(具体作用域)。
>
> 箭头函数，适合与this无关的回调，定时器，数组的方法回调。箭头函数不适合 与 this有关的回调，事件回调，对象的方法



### 函数参数默认值

ES6 允许给函数参数赋值初始值

+ 形参初始值 具有默认值的参数，一般要靠后(潜规则)

  ```javascript
  function add (a, b, c=10) {
      return a + b + c;
  }
  console.log(add(1,2));
  ```

+ 与解构赋值结合

  ```javascript
  function connect({host='127.0.0.1', username,password,port}){
      let host = host;
      let username = username;
  }
  connect({
      host:'localhost',
      username:'root',
      password:'soft01',
      port:'3306'
  })
  ```

### rest 参数

ES 6 引入rest 参数，用于获取函数的实参，用来代替 arguments

```javascript
// ES5 arguments 获取实参的方式
function date () {
    console.log(arguments); // 是一个对象
}
date('a','b','c','d');

// ES6 rest 参数
function date (...args) {
    console.log(args);// 是一个数组
}
date('a','b','c','d');
```

> rest 参数必须要放到参数的最后



### 扩展运算符

[...] 扩展运算符能将[数组] 转换为逗号分隔的[参数序列]

```javascript
// 声明一个数组 ...
    const tfboys = ['易烊千玺', '王源', '王俊凯']; // => '易烊千玺', '王源', '王俊凯'

// 声明一个函数
function chunwan() {
    console.log(arguments);
}
chunwan(tfboys);
chunwan(...tfboys); // 等同于 chunwan('易烊千玺', '王源', '王俊凯')
```

+ 数组的合并

  ```javascript
  const kuaizi = ['王太利', '肖央'];
  const fenghuang = ['曾毅', '玲花'];
  console.log(kuaizi.concat(fenghuang));// '王太利', '肖央','曾毅', '玲花'
  const kuaizifenghuang = [...kuaizi, ...fenghuang];
  console.log(kuaizifenghuang);// '王太利', '肖央','曾毅', '玲花'
  ```

+ 数组的克隆

  ```javascript
  const sanzhihua = ['E', 'G', 'M'];
  const sanyecao = [...sanzhihua]; // ['E', 'G', 'M']
  console.log(sanyecao);// 'E', 'G', 'M'
  ```

+ 将伪数组转为真正的数组

  ```javascript
  const divs = document.querySelectorAll('div');
  console.log(divs);
  const divArr = [...divs];
  console.log(divArr);
  ```



### Symbol 数据类型

+ 创建Symbol

  + 方式1 Symbol()

    ```javascript
    let s = Symbol();
    console.log(s, typeof s);// Symbol() "symbol"
    let s2 = Symbol('尚硅谷');
    let s3 = Symbol('尚硅谷');
    console.log(s2 === s3);// false
    ```

  + 方式2 Symbol.for();

    ```javascript
    let s4 = Symbol.for('尚硅谷');
    let s5 = Symbol.for('尚硅谷');
    console.log(s4, typeof s4);// Symbol('尚硅谷') "symbol"
    console.log(s4 === s5);// true
    ```

> 不能进行数据运算和比较

