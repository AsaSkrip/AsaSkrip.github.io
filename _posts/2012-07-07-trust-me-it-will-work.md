---
date: 2018-03-12 12:26:40
layout: post
title: JS基础面试题
subtitle: 40道JS基础面试题
description: 40道JS基础面试题
image: https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559821648/theme1_eoyjtl.jpg
optimized_image: https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559821648/theme1_eoyjtl.jpg
category: 'JS基础面试题'
tags:
  - languages
  - tips
author: mranderson
---

<a name="CQin7"></a>

# JS基础

<a name="Gruog"></a>

## 1、js的数据类型有哪些

```
答: 简单数据类型: number string boolean undefined null symbol
	复杂数据类型: object  function  array
```

<a name="Zj01o"></a>

## 2、返回false的情况有哪些

```
答: 0  ""   null  false  NaN  undefined  不成立的表达式
```

<a name="H1w0q"></a>

## 3、两个等号和三个等号的区别

```javascript
答：== 表示是相等，只比较值。在比较时，会将两边的值转成相同类型的值，然后比较。
   === 表示是全等，不仅比较值，也比较类型
```

<a name="AxBD0"></a>

## 4、null和undefined的区别

```javascript
答：null 表示空值 没有获取到。typeof null 返回"object"
   undefined 表示未定义，声明没有值。typeof undefined 返回"undefined"
```

<a name="LnACW"></a>

## 5、JSON字符串和JS对象怎么相互转换（序列化）

```
答: JS对象转JSON字符串: JSON.stringify(对象)
    JSON字符串转JS对象: JSON.parse(字符串)
```

<a name="OqgLR"></a>

## 6、伪数组和真数组的区别

```javascript
伪数组：
1、拥有length属性
2、不具有数组的方法
3、伪数组是一个Object，真数组是Array
4、伪数组的长度不可变，真数组的长度是可变的
```

<a name="Wt2ur"></a>

## 7、那些情况会得到伪数组

```javascript
1、参数 arguments，
2、DOM 对象列表（比如通过 document.getElementsByTags 得到的列表）、childNodes也是伪数组
3、jQuery 对象（比如 $("div")）
```

<a name="vWTHZ"></a>

## 8、伪数组怎么转换为真数组

```javascript
1、let newArr = Array.protype.slice.call(伪数组)
2、let newArr = Array.from(伪数组),ES6的新语法
3、let newArr = [...伪数组]，使用扩展运算符,也是ES6的语法
```

<a name="ttrgE"></a>

## 9、let、const、var的区别

```javascript
1、var声明变量存在提升（提升当前作用域最顶端），let和const是不存在变量提升的情况
2、var没有块级作用，let和const存在块级作用域
3、var允许重复声明，let和const在同一作用域不允许重复声明
4、var和let声明变量可以修改，const是常量不能改变
```

<a name="M4U3p"></a>

## 10、for in 和 for of 的区别

```javascript
1、for…in是遍历数组、对象的key
2、for…of是遍历数组的value
例如：
let arr = ["a","b"];
1）for (let key in arr) {
console.log(key);  //0 1
}
2）for (let value of arr) {
console.log(value);  //a b
}
```

<a name="UevYJ"></a>

## 11、说下typeof返回的数据类型

**回答：**<br />①：简单数据类型直接返回对应的英文，比如：number  string boolean undefined symbol等，特殊情况， null 返回 object<br />②：复杂数据类型返回 object， 函数返回的是 function

<a name="eb821d79"></a>

## 12、请说说你对作用域链的理解？

**回答**：<br />①：JavaScript中的作用域分为全局作用域、局部作用域、块作用域。多个嵌套的作用域形成作用域链。<br />②：作用域链描述了变量的查找机制，当在某个作用域中查找变量时，如果当前 作用域没有找到，则向上层作用域查找，上层没有，继续向上层查找，一直找到全局作用域。找到则使用该变量，没有找到则报错。
<a name="bb9aa7e2"></a>

## 13、简单数据类型与复杂数据类型在内存上存储有什么区别？

**回答：**<br /> ①：基本类型主要为以下6种：Number、String、Boolean、Undefined、null、symbol

   - 基本数据类型的值存储在 栈中

②：引用类型  Object、Array、Function  

   - 引用类型的值存储于 堆中
     <a name="z7qcx"></a>

# 三、webapi

<a name="T9g6k"></a>

## 14、localStorage、sessionStorage和cookie的区别

```
答: 共同点: 都是保存在浏览器端，且同源的。
	区别: 
	1. 请求不同: 
		cookie 数据始终在同源的http请求中携带（即使不需要），即cookie在浏览器和服务器间来回传递。
				sessionStorage 和 localStorage不会自动把数据发给服务器，仅在本地保存。
	2. 存储大小限制也不同: 
		cookie 数据不能超过4k，同时因为每次http请求都会携带cookie，所以cookie只适合保存很小的数据，如会话标识。
		sessionStorage 和 localStorage虽然也有存储大小的限制，但比cookie大得多，sessionStorage约5M、localStorage约5M 。
	3. 数据有效期不同: 
		 sessionStorage：仅在当前浏览器窗口关闭前有效，自然也就不可能持久保持； 
		 localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；
		 cookie只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭。 
	4. 作用域不同:
		sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面；
		localStorage在所有同源窗口中都是共享的；
		cookie也是在所有同源窗口中都是共享的。
```

<a name="5809d5c1"></a>

## 15、请说下什么是重绘和重排（回流）？他们的区别是什么？

**回答：**<br />**重排**: 也叫做回流，当DOM元素影响了元素的几何属性（例如宽和高），浏览器需要重新计算元素的几何属性，同样其它元素的几何属性也会和位置也会因此受到影响。浏览器会使渲染树中受到影响的部分失效，并重新构造渲染树。这个过程称为“重排”。<br />**重绘**: 完成重排后，浏览器会重新绘制受影响的部分到屏幕上中，该过程称为“重绘”。<br />**总结：**<br />当我们改变DOM的大小，增加删除都会导致重排，当给DOM元素改变颜色的时候，会导致重绘，重排一定会重绘，重绘不会重排。重排会影响性能，所以我们尽快能的减少重排的操作（这句话是重点）
<a name="f96ccd71"></a>

## 16、事件流分为哪两个阶段？

事件流是指事件传播的顺序，由事件捕获 => 目标事件 => 事件冒泡<br />所以事件流分为捕获和冒泡两个阶段。
<a name="git8R"></a>

## 17、事件委托的实现原理？如果获取当前触发的dom节点？

回答：<br />①：事件委托主要利用事件冒泡特性来实现的。<br />②：事件委托（事件委派）主要有2个使用场景：

- 如果有多个子元素，可以把事件注册给父元素，因为点击子元素，也会将事件冒泡到其父元素上，利用这个特点提高了性能。
- 给后来动态生成的元素绑定事件。因为动态生成的元素没有办法直接绑定事件，可以利用事件委托来绑定事件。

使用 e.target 获取当前触发事件的元素。
<a name="YAXcZ"></a>

## 18、如何阻止冒泡和默认行为

```javascript
答: 阻止冒泡和捕获  e.stopPropagation()
    阻止默认行为   e.preventDefault()   return false
    注意：addEventListener注册的事件，在高浏览器版本中，return false将没有效果，必须要用事件对象
```

<a name="hPnPq"></a>

## 19、原生注册事件的方式有哪些？区别是什么

```javascript
答: 注册方式
		  1. on + 事件名称
		  2. addEventListener
		区别: 
			1. 使用on注册事件,同一个元素只能注册一个同类型事件,否则会覆盖。
			2. addEventListener可以注册同一事件多次,不会被覆盖。
```

<a name="Cc7dL"></a>

# 四、JS高级

<a name="J0Rw1"></a>

## 20、说说你对this的理解

**回答：**<br />this是个关键字,它的指向和函数的调用方式有关， 初步的理解就是，**this指向所在函数的调用者。**<br />1、 以函数形式调用时， this 永远都是 window<br />2、 以方法的形式调用时， this 是调用方法的对象<br />3、 以构造函数的形式调用时， this 是新创建的那个对象<br />4、 使用 call 和 apply 调用时， this 是指定的那个对象<br />5、 箭头函数： 箭头函数的 this 按照普通变量对待。比如把他当做 x 变量即可，然后按照作用域链找就行了。<br />6、全局中的this是window<br />7、事件处理函数，如果是普通的function函数，则this指向事件源。
<a name="I4Xuw"></a>

## 21、new操作符做了什么

```
答:  1. 创建一个新对象
	2. 函数内部的this指向这个对象
	3. 执行函数体
	4. 自动返回这个函数
```

<a name="MOm92"></a>

## 22、什么是深拷贝什么是浅拷贝

```
答: 浅拷贝: 拷贝对象的一层属性,如果对象里面还有对象,拷贝的是地址, 两者之间修改会有影响,适用于对象里面属性的值是简单数据类型的.
    深拷贝: 拷贝对象的多层属性,如果对象里面还有对象,会继续拷贝,使用递归去实现.
```

<a name="U2dsC"></a>

## 23、如何实现深拷贝和浅拷贝

浅拷贝：<br />Object.assign()<br />{ ...obj }<br />lodash 库的 clone() 方法<br />手写循环<br />深拷贝：<br />lodash 库的 cloneDeep() 方法<br />JSON.parse(JSON.stringify(被拷贝的对象)) -- 有缺陷，不能拷贝函数<br />手写循环 + 递归
<a name="fUzTv"></a>

## 24、如何用递归实现深拷贝？

```javascript
function copy(oldD) {
    let newD  // 新数据
    // 需要判断oldD 何方数据类型？
    // ************************************数组
    if(oldD instanceof Array){
      newD = []
      for (let i = 0; i < oldD.length; i++) {
        let val = oldD[i]  // 每一项数据
        val = copy(val) // val
        newD.push(val)
      }
    }
    // ***********************************对象
    else if(oldD instanceof Object){
      newD = {}
      for (let key in oldD) {
        let val = oldD[key]  // 每一项数据，有可能又是简单数组
        val = copy(val)  // val不能直接赋值，需要经过copy
        newD[key] = val  // 添加键值对
      }
    }
    
    // ***********************************简单数据
    else {
      newD = oldD
    }
    return newD 
  }
```

<a name="U7Vwr"></a>

## 25、描述下垃圾回收机制？

首先:垃圾回收机制内部算法：引用计数 和 标记清除<br />接下来：

- 引用计数：把堆上对象能够访问次数记下来，如果发现某个对象计数为0，算法认为没有变量访问这个对象。该对象所占空间，判定是垃圾，进行回收！但是：如果两个对象相互引用，各自计数永远不会为0，不会判定为是垃圾，不会回收！所以：主流浏览器不再使用该算法！
- 标记清除：核心就是 从 使用对象次数  到 无法到达对象；只要是堆上对象无法访问，哪怕是对象相互引用，但是无法访问，算法对该对象标记为垃圾空间！
  <a name="XAm4g"></a>

## 26、对闭包是怎么理解的？

答：

- 基本形式：两个嵌套关系的函数,内部函数可以访问外部函数定义的局部变量，那么该变量与内部函数就构造了闭包的形式
- 优点：形成私有空间，避免全局变量的污染
- 缺点：持久化内存，导致内存泄露
- 解决：
  - 1、尽快避免函数的嵌套，以及变量的引用
  - 2、执行完的变量，可以赋值null，触发垃圾回收机制，进行回收释放内存
    <a name="fuii3"></a>

## 27、什么是原型对象和原型链

答：<br />原型对象：每个构造函数都有prototype属性，这个属性的值是个对象，称之为原型对象！<br />原型链：对象都有__proto__属性,这个属性指向它的原型对象,原型对象也是对象,也有__proto__属性,指向原型对象的原型对象,这样一层一层形成的链式结构称为原型链.<br />    

<a name="faLdZ"></a>

## 28、原型链有什么意义？

总得来说：给实例化对象上调用方法或使用某个属性，提供查询机制！<br />具体查询：<br />先在实例化对象本身上去找该方法！<br />如果没有，去实例化对象的__proto__（原型对象上去找）<br />如果当前原型对象上还没有该方法，继续往原型对象上的原型对象上去找<br />如果还是没有找到，报错  对象.xxx is not function
<a name="B60Mw"></a>

## 29、call、apply和bind的区别

答: <br />1、call和apply方法都可以调用函数,方法内的第一个参数可以修改this的指向<br />2、call方法可以有多个参数,除了第一个参数,其他参数作为实参传递给函数；apply方法最多有2个参数,第二个参数是个数组或伪数组,数组里面的每一项作为实参传递给函数<br />3. bind方法不能调用函数,它会创建一个副本函数,并且该新函数的this指向已经被改变！

<a name="yjFyJ"></a>

## 30、怎么理解函数的防抖和节流

防抖：就是指触发事件后，**在n秒后**对应的函数会执行！如果**在n秒中**又触发了事件，则会重新计算函数执行时间。<br />节流：就是指连续触发事件，如果上一次触发的对应的执行函数没有执行完成，下一次触发是不会引起对应代码执行的
<a name="JH8gH"></a>

## 31、es6-es10新增常用方法

```javascript
答: 
es6:
1、let、const
2、解构赋值  let { a, b } = { a: 1, b: 2 }
3、箭头函数
4、字符串模板
5、扩展运算符
6、数组方法：map、filter等等
7、类：class关键字
8、promise
9、函数参数默认值 fn(a = 1) {}
10、对象属性简写 let a = 1; let obj = {a}
11、模块化：import--引入、exprot default--导出

es7:
1、includes()方法，用来判断一个数组是否包含一个指定的值，根据情况，如果包含则返回true，否则返回false。

es8:
1、async/await

es9：
1、Promise.finally() 允许你指定最终的逻辑

es10:
1、数组Array的flat()和flatmap()
   flat:方法最基本的作用就是数组降维
      var arr1 = [1, 2, [3, 4]];
            arr1.flat(); 
            // [1, 2, 3, 4]

        var arr3 = [1, 2, [3, 4, [5, 6]]];
        arr3.flat(2);
        // [1, 2, 3, 4, 5, 6]

        //使用 Infinity 作为深度，展开任意深度的嵌套数组
        arr3.flat(Infinity); 
        // [1, 2, 3, 4, 5, 6]
   flatmap:方法首先使用映射函数映射(遍历)每个元素，然后将结果压缩成一个新数组
```

<a name="WHLKL"></a>

## 32、怎么理解同步和异步

```javascript
	1、javascript是单线程。单线程就意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。如果前一个任务耗时很长，后一个任务就不得不一直等着。于是就有一个概念——任务队列。
	2、同步任务，顾名思义，就是立即执行的任务，同步任务一般会直接进入到主线程中执行；而异步任务，就是异步执行的任务，比如ajax网络请求，setTimeout 定时函数等都属于异步任务，异步任务会通过任务队列( Event Queue )的机制来进行协调。
```

<a name="PU2bl"></a>

## 33、js的运行机制是什么

```javascript
答：js是单线程执行的，页面加载时，会自上而下执行主线程上的同步任务，当主线程代码执行完毕时，才开始执行在任务队列中的异步任务。具体如下  
    1.所有同步任务都在主线程上执行，形成一个执行栈。
    2.主线程之外，还存在一个"任务队列(eventloop队列或者消息队列)"。只要异步任务有了运行结果，就在"任务队列"之中放置一个事件。
    3.一旦"执行栈"中的所有同步任务执行完毕，系统就会读取"任务队列"，看看里面有哪些事件。哪些对应的异步任务，于是结束等待状态，进入执行栈，开始执行。
    4.主线程不断重复上面的第三步。
```

<a name="Sv3wy"></a>

## 34、怎么理解面向对象

```javascript
答：1、面向对象是一种软件开发的思想和面向过程是相对应的，就是把程序看作一个对象，将属性和方法封装其中，以提高代码的灵活性、复用性、可扩展性。
  2、面向对象有三大特性：封装、继承、多态。
       封装：把相关的信息（无论数据或方法）存储在对象中的能力
       继承：由另一个类（或多个类）得来类的属性和方法的能力
       多态：编写能以多种方法运行的函数或方法的能力
   3、js中对象是一个无序的数据集合或者也可以说是属性和方法的集合，可以动态的添加属性可方法。
   4、js是基于对象，但是也使用了嵌入了面向对象的思想，可以实现继承和封装，这样也可以提供代码的灵活性和复用性。
```

<a name="FjMXH"></a>

## 35、异步函数有哪些

```javascript
JavaScript 中常见的异步函数有：定时器，事件和 ajax 等
```

<a name="uyS1z"></a>

## 36、数组如何进行降维（扁平化）

```javascript
1、利用Array.some方法判断数组中是否还存在数组，es6展开运算符连接数组
       let arr = [1,2,[3,4]]
        while (arr.some(item => Array.isArray(item))) {
            arr = [].concat(...arr);
        }
2、使用数组的concat方法
　   let arr = [1,2,[3,4]]
     let result = []
     result = Array.prototype.concat.apply([], arr)

3、 使用数组的concat方法和扩展运算符
    var arr = [1,2,[3,4]]
    var result = []
    result = [].concat(...arr)
        
4、es6中的flat函数也可以实现数组的扁平化
    let arr = [1,2,['a','b',['中','文',[1,2,3,[11,21,31]]]],3];
    let result = arr.flat( Infinity )
    注意：flat方法的infinity属性，可以实现多层数组的降维
```

<a name="CdI7S"></a>

## 37、什么是作用域链

```javascript
	1、作用域：分全局作用域和局部作用域
    2、在访问一个变量时，首先在当前作用域中找，如果找不到再到外层作用域中找，这样一层一层的查找，就形成了作用域链。
    3、如果没有找到会返回undefined
```

<a name="xgAmb"></a>

## 38、数组去重的方式

```javascript
1、第一种方式：利用indexof方法
  let arr = [2, 8, 5, 0, 5, 2, 6, 7, 2]
  let newArr = []
  for (let i = 0; i < arr.length; i++) {
     if (newArr.indexOf(arr[i]) === -1) {
       newArr.push(arr[i])
     }
  }

2、第二种方式：sort()方法
   let arr = [2, 8, 5, 0, 5, 2, 6, 7, 2]
   arr.sort()
   let newArr = [arr[0]]
   for (let i = 1; i < arr.length; i++) {
     if (arr[i] !== newArr[newArr.length - 1]) {
       newArr.push(arr[i])
     }
   }

3、第四种方式：利用ES6 Set去重
 let arr = [2, 8, 5, 0, 5, 2, 6, 7, 2, 8]
 let newArr = new Set(arr)
```

<a name="PRr1E"></a>

## 39、斐波那契数列

```javascript
  // 斐波那契数列
  function fiB(n) {
    if (n == 1 || n == 2) {
        return 1
      }
        return fn(n - 1) + fn(n - 2)
   }
    console.log(fiB(10))
```

<a name="corXl"></a>

## 40、你能说说怎么理解事件循环机制的？

**回答：**<br />1、JavaScript 是一门单线程语言. 单线程可能会出现阻塞的情况，所js分了同步任务和异步任务。<br />2、同步和异步任务分别进入不同的执行环境，同步的进入主线程，即主执行栈，异步的进入 任务队列。<br />3、主线程内的任务执行完毕为空，会去 任务队列 读取对应的任务，推入主线程执行。 上述过程的不断重复就是我们说的 Event Loop (事件循环)。










