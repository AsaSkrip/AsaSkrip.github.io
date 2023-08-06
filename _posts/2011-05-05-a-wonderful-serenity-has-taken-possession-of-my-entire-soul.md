---
date: 2018-07-20 12:26:40
layout: post
title: VUE基础面试题
subtitle: 50道Vue常见面试题集锦，涵盖入门到精通，自测 Vue 掌握程度
description: Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
image: https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559820489/js-code_n83m7a.jpg
optimized_image: https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559820489/js-code_n83m7a.jpg
category: VUE面试题
tags:
  - VUE
  - 面试题
author: 李梓涵
---


# 一、路由

<a name="zgfYl"></a>

## 1、Vue-router 路由有哪些模式

```javascript
一般有两种模式：
        1、hash 模式：后面的 hash 值的变化，浏览器既不会向服务器发出请求，浏览器也不会刷新，每次 hash 值的变化会触发 hashchange 事件。
        2、history 模式：利用了 HTML5 中新增的 pushState() 和 replaceState() 方法。这两个方法应用于浏览器的历史记录栈，在当前已有的 back、forward、go 的基础之上，它们提供了对历史记录进行修改的功能。只是当它们执行修改时，虽然改变了当前的 URL，但浏览器不会立即向后端发送请求。
```

<a name="hZR6b"></a>

## 2、vue中$route和$router有什么区别？

this.$router 是 router 实例，也就是 router/index.js 中导出的那个对象，通过它可以调用 go、push**等**方法进行页面跳转。<br />this.$route 表示当前访问的路由。通过 this.$route 可以获取到当前路由信息，比如获取当前路由的完整地址、query参数、params参数、meta信息等等。这个属性是只读的，不过可以通过 watch侦听到它的变化。
<a name="YIMjv"></a>

## 3、路由间是怎么跳转的，有哪些方式？

1、<router-link to="需要跳转到页面的路径"> <br />2、this.$router.push()跳转到指定的 url，并添加一条历史记录。<br />3、this.$router.replace()跳转到指定的 url，但是不会增加一条历史记录。<br />4、this.$router.go(n)前进或后退 。
<a name="aSMDC"></a>

## 4、怎么定义vue-router的动态路由，怎么获取传过来的动态参数？

> 动态路由就是 路径参数

1. 定义路由规则的时候，需要在path里面设置好 "斜线冒号变量"（/path/:id/:age）这种规则
2. 当地址栏或跳转地址 和 路由规则匹配的时候，会进入对应的组件
3. 组件中，通过 `$route.params.参数名`的语法获取参数值

| **类型**             | **hash地址**    | **路由规则**                 | **组件中获取参数值** |
| -------------------- | --------------- | ---------------------------- | -------------------- |
| 路径参数（动态路由） | /movie/3/绿皮书 | { path: '/movie/:id/:name' } | $route.params.参数名 |

<a name="KSaZG"></a>

## 5、路由传参的方式和区别

```javascript
答: 
1、方式：params 和 query
2、区别：1）params用的是name，传递的参数在地址栏不会显示，类似于post
        2）query用的是path,传递的参数会在地址栏显示出来，类似于get      
3、举例说明：
   1）params 传参
    传： this.$router.push({
          name: 'particulars',
          params: {
            id: id
          }
        })
     接：this.$route.params.id
     
   2）query传参
     传：this.$router.push({
          path: '/particulars',
          query: {
            id: id
          }
        })
      接：this.$route.query.id
```

<a name="rPHWK"></a>

# 二、生命周期

<a name="Fi10l"></a>

## 6、vue生命周期分为几个阶段？

Vue 实例从创建到销毁的过程，就是生命周期。<br />可以分为三个阶段：创建阶段、数据更新阶段、销毁阶段。<br />追问：创建阶段会执行哪些钩子函数？<br />答：创建阶段会依次执行 beforeCreate、created、beforeMount 和 mounted 4个钩子函数。<br />追问：更新阶段会执行哪些钩子函数？<br />答：更新阶段会依次执行 beforeUpdate 和 updated 两个钩子函数。<br />追问：销毁阶段会执行哪些钩子函数？<br />答：销毁阶段会依次执行 beforeDestroy和destroyed两个钩子函数。
<a name="IcPKJ"></a>

## 7、第一次加载页面会触发哪几个钩子函数？

当页面第一次加载时会触发 beforeCreate, created, beforeMount, mounted 这几个钩子函数 。<br />如果是动态组件，并设置了缓存该组件，则还会触发 activated 钩子函数。
<a name="Rpt7T"></a>

## 8、Vue 的父组件和子组件生命周期钩子函数执行顺序

```javascript
1、Vue 的父组件和子组件生命周期钩子函数执行顺序可以归类为以下 4 部分：
  1）加载渲染过程
     父 beforeCreate -> 父 created -> 父 beforeMount -> 子 beforeCreate -> 子 created -> 子 beforeMount -> 子 mounted -> 父 mounted
  2）子组件更新过程
     父 beforeUpdate -> 子 beforeUpdate -> 子 updated -> 父 updated
  3）父组件更新过程
     父 beforeUpdate -> 父 updated
  4）销毁过程
  父 beforeDestroy -> 子 beforeDestroy -> 子 destroyed -> 父 destroyed
```

<a name="yyTv7"></a>

## 9、vue 钩子函数有哪些，有哪些使用的场景

```javascript
1、各阶段包含钩子： 
		beforeCreate  在data数据注入到vm实例之前，此时vm身上没有数据
    created       在data数据注入到vm实例之前，此时vm身上有数据

    beforeMount   生成的结构替换视图之前，此时DOM还没更新
    mounted       生成的结构替换视图之前，此时DOM已经更新完成

    beforeUpdate  数据变化了，dom更新之前
    updated       数据变化了，dom更新之后
    
    activated     被keep-alive缓存的组件激活时调用
    deactivated   被keep-alive缓存的组件停用时调用

    beforeDestroy 实例销毁之前调用，组件实例仍然可用
    destroyed     实例销毁之后调用

    这些钩子函数会在vue的生命周期的不同阶段，自动被vue调用

2、常用的钩子函数使用场景：
    beforeCreate  做loading的一些渲染
    created       结束loading， 发送数据的请求，拿数据
    mounted       可以对dom进行操作
    updated       监视数据的更新
    beforeDestroy 销毁非vue资源，防止内存泄漏，例如清除定时器
    activated     当我们运用了组件缓存时，如果想每次切换都发送一次请求的话，需要把请求函数写在activated中，而写在created或mounted中其只会在首次加载该组件的时候起作用。
```

<a name="rW3aG"></a>

# 三、指令、方法、...

<a name="IobgN"></a>

## 10、v-show和v-if指令的共同点和不同点？

共同点：都可以通过条件控制元素的显示隐藏；<br />不同点：

1. v-show通过display样式控制元素的显示和隐藏
2. v-if 通过创建、移除元素控制元素的显示和隐藏
3. 对于v-show而言，无论条件如何都会先创建元素，然后再通过display样式控制显示隐藏，有更高的初始渲染开销
4. 如果用 v-if 频繁切换元素显示隐藏，就会不断的创建移除元素，开销很大。
   <a name="mUkOJ"></a>

## 11、为什么避免v-if和v-for一起用？

Vue2中，v-for 比 v-if 具有更高的优先级。如果同时使用，那么当条件为false时，也会先完成遍历，遍历之后在根据条件判断是否显示，无疑会造成很多性能的浪费。比如下面的例子：

```html
循环了1000次，结果一个都不需要显示。白白浪费性能
<div v-for="item in 1000" v-if="false">xxxxxxxxxxx</div>
```

参考链接：[点这里](https://v2.cn.vuejs.org/v2/guide/list.html#v-for-%E4%B8%8E-v-if-%E4%B8%80%E5%90%8C%E4%BD%BF%E7%94%A8)

Vue3中，v-if 比 v-for 具有更高的优先级。如果同时使用，v-if 将不能使用v-for中的变量。比如：

```html
先执行v-if ，条件是item < 100。但此时for还没执行呢，拿不到item
<div v-for="item in 1000" v-if="item < 100">xxxxxxxxxxx</div>
```

参考链接：[点这里](https://cn.vuejs.org/guide/essentials/list.html#v-for-with-v-if)
<a name="WF0Zb"></a>

## 12、事件修饰符和按键修饰符有哪些

```javascript
事件修饰符：
	.prevent  阻止事件默认行为
    .stop     阻止事件冒泡
    .capture  设置事件捕获机制
    .self     只有点击元素自身才能触发事件
    .once     事件只触发一次
 按键修饰符：
    .tab
    .enter
    .esc
    .space
    .delete(捕获"删除"和"回退"键)
    .up
    .down
    .left
    .right
```

<a name="wdaN6"></a>

## 13、v-model修饰符有哪些

```javascript
.trim   去除首尾空格
.lazy   只在输入框失去焦点或按回车键时更新内容，不是实时更新
.number 将数据转换成number类型(原本是字符串类型)
```

<a name="yP1pA"></a>

## 14、v-model的原理是什么

```javascript
1、v-model主要提供了两个功能，view层输入值影响data的属性值，属性值发生改变会更新层的数值变化.
2、v-model指令的实现：
	3.1 v-bind:绑定响应式数据
	3.2 触发input事件并传递数据 (核心和重点)
3、其底层原理就是(双向数据绑定原理)：
	3.1 一方面modal层通过defineProperty来劫持每个属性，一旦监听到变化通过相关的页面元素更新。
    3.2 另一方面通过编译模板文件，为控件的v-model绑定input事件，从而页面输入能实时更新相关data属性值。
```

<a name="s8uNa"></a>

## 15、v-for中为什么要加key

```javascript
作用：
      1.key的作用主要是为了高效的更新虚拟DOM，提高渲染性能。
      2.key属性可以避免数据混乱的情况出现。
原理：
      1.vue实现了一套虚拟DOM，并希望"就地更新"节点
      2.当数据发生变化时，会使用Diff算法比较新旧虚拟DOM。
      3.使用key给每个节点做一个唯一标识，在进行Diff算法的时候就会比较key值相同的节点，提高性能。
```

<a name="ysNZp"></a>

## 16、v-on可以监听多个方法吗

```javascript
可以
例如：
<input type="text" v-on="{ input:onInput,focus:onFocus }">
```

<a name="q9rtI"></a>

## 17、什么是vue的计算属性？

通过计算得来的属性，就是计算属性。

- 定义在 computed 中的方法，使用时，要当做属性用（不要加小括号）
- 依赖数据改变，计算属性会自动重新计算
- 会有缓存特点，多次调用，只会计算一次
- 如果设置 set 方法，也可以直接修改计算属性，修改时，会触发set方法
  <a name="gOCL5"></a>

## 18、watch、methods、computed的区别？

计算属性computed：<br />1、支持缓存，只有依赖数据发生改变，才会重新进行计算<br />2、不支持异步，当computed内有异步操作时无效，无法监听数据的变化<br />3、如果computed需要对数据修改，需要写get和set两个方法，当数据变化时，调用set方法。<br />4、computed擅长处理的场景：一个结果受多个数据影响，例如购物车计算总价

侦听属性watch：<br />1、不支持缓存，数据变，直接会触发相应的操作；<br />2、watch支持异步；可以监听ajax响应结果的变化；<br />3、支持 immediate和 deep 配置<br />5、watch擅长处理的场景：一个数据改变影响多个结果

方法methods：<br />1、不会自动执行，需要调用才会执行<br />2、结果不会缓存，每调用一次，就会执行一次
<a name="AuNpO"></a>

## 19、怎么在watch监听开始之后立即被调用？

在选项参数中指定 immediate: true 

```javascript
watch: {
  xxx: {
    handler () {},
    immediate: true
  }
}
```

<a name="vyuAo"></a>

## 20、watch的属性用箭头函数定义结果会怎么样

```javascript
不应该使用箭头函数来定义 watch :
例如：
    watch: {
      a: () => {  //  这里不应该用箭头函数
        console.log(this);
        this.sum = this.a + this.b;
      }
    })。
理由是箭头函数绑定了父级作用域的上下文，所以 this 将不会按照期望指向 Vue 实例，
this.a 将是 undefined。

注意：methods里面定义的方法也不要用箭头函数
```

<a name="WZw5m"></a>

## 21、computed、data、methods、props可以同名吗？

不能同名，因为不管是 computed 属性名还是 data 数据名还是 props 数据名，还是methods方法，都 会被挂载在 vm 实例上，因此这几个都不能同名。 
<a name="Pf4TS"></a>

## 22、vue组件中的data为什么必须是函数？

1、每个组件都是 Vue 的实例。<br />2、组件共享 data 属性，当 data 的值是同一个引用类型的值时，改变其中一个会影响其他。<br />3、组件中的 data 写成一个函数，数据以函数返回值形式定义，这样每复用一次组件，就会返回一份新的 data，类似于给每个组件实例创建一个私有 的数据空间，让各个组件实例维护各自的数据。而单纯的写成对象形式， 就使得所有组件实例共用了一份 data，就会造成一个变了全都会变的结果。 
<a name="CobCY"></a>

# 四、组件

<a name="NOD3E"></a>

## 23、你知道style加scoped属性的用途和原理吗

```javascript
用途：防止全局同名CSS污染
原理：在标签加上v-data-something属性，再在选择器时加上对应[v-data-something]，即CSS带属性选择器，以此完成类似作用域的选择方式.
	scoped会在元素上添加唯一的属性（data-v-x形式），css编译后也会加上属性选择器，从而达到限制作用域的目的。
```

<a name="OHbQG"></a>

## 24、$nextTick是什么？原理是什么

```javascript
背景：
	1、简单来说，Vue 在修改数据后，视图不会立刻更新，而是等同一事件循环中的所有数据变化完成之后，再统一进行视图更新。
    
定义：
	2、在下次 DOM 更新循环结束之后执行延迟回调。在修改数据之后立即使用这个方法，获取更新后的 DOM。nextTick()，是将回调函数延迟在下一次dom更新数据后调用，简单的理解是：当数据更新了，在dom中渲染后，自动执行该函数。
    
原理
	3、vue用异步队列的方式来控制DOM更新和nextTick回调先后执行。
	简单来说，nextTick是做了promise加上setTimeout的封装,利用事件换行机制，来确保当nextTick出现时，都是在我们所有操作DOM更新之后的。

场景：
	4.1 点击获取元素宽度
    4.2 使用swiper插件通过 ajax 请求图片后的滑动问题
    4.3 点击按钮显示原本以 v-show = false 隐藏起来的输入框，并获取焦点
```

<a name="SNund"></a>

## 25、vue组件间是如何进行传值的？					 			

1）父组件向子组件传递数据 。

- 父组件内，在使用子组件时，通过自定义属性向子组件传递数据；
- 子组件通过 props 接收即可 

2）子组件向父组件传递数据 。

- 子组件通过 $emit 触发事件，并携带参数的方式向父组件传输数据
- 父组件设置事件，并通过事件触发方法的形参来接收数据

3）非父子组件之间传递数据

- 非父子组件可以使用 eventBus 方案进行数据传递

4）另外，也可以使用 vuex 进行组件间的数据共享<br />代码参考：

```javascript
1、父传子
    通过props传递
    父组件： <child :list = 'list' />
    子组件: props['list'],接收数据,接受之后使用和data中定义数据使用方式一样

2、子传父
	在父组件中给子组件绑定一个自定义的事件，子组件通过$emit()触发该事件并传值。
    父组件： <child @receive = 'getData' />
            getData(value){value就是接收的值}
    子组件: this.$emit('receive',value)

3、兄弟组件传值
	通过中央通信 let bus = new Vue()
    A组件：methods :{ 
    	    		sendData(){
                bus.$emit('getData',value)
              }
           } 发送
    B组件：created(){
        		bus.$on(‘getData’,(value)=>{value就是接收的数据})
    			} 进行数据接收
```

<a name="nakdC"></a>

## 26、谈谈你对slot的了解

slot就是插槽，主要是封装组件的时候，用它来占位。<br />然后其他组件使用这个封装的组件的时候，给 slot 提供页面结构。

```javascript
1 默认插槽  在子组件中写入slot，slot所在的位置就是父组件要显示的内容
2 具名插槽  在子组件中定义了多个slot标签，则需要通过name属性来区分这些插槽，加入了name属性的插槽就是具名插槽。
    			 在父组件中使用template并写入对应的slot名字来指定该内容在子组件中现实的位置
3 作用域插槽  在子组件的slot标签上绑定需要的值<slot :data="user"></slot>
    	        在父组件上使用 v-slot:插槽名="user"  或  #插槽名="user" 来接收子组件传过来的值
```

<a name="t939j"></a>

## 27、请说下封装vue组件的过程。

封装组件就是为了复用，可以提升整个项目的开发效率。<br />封装的大致逻辑：<br />1）根据需求，把可以复用的结构，样式以及功能，单独抽离成一个组件，主要是为了实现复用嘛。<br />2）封装的组件，一般会放到 components 文件夹里面，并且在main.js中注册，方便在其他组件中调用。<br />3）传递数据的话，就是父传子或子传父。<br />4）需要传递页面结构的话，就用插槽。<br />5）还有，vue3中，如果需要 父组件主动调用子组件的方法 可以在 methods 选项中开放方法
<a name="FWazk"></a>

## 28、vue是如何获取DOM

```javascript
1、先给标签设置一个ref值，再通过this.$refs.domName获取，这个操作要在mounted阶段进行。
2、例如：
<template>
	<div ref="test"></div>
</template>
mounted(){
   const dom = this.$refs.test 
}
```

<a name="bAGE0"></a>

## 29、vue该如何实现组件缓存？

使用<keep-alive></keep-alive> 包裹动态组件，即可实现动态组件的缓存。<br />可以通过include 属性设置哪些组件需要被缓存，也可以通过exclude设置哪些组件不需要被缓存。
<a name="ep4xW"></a>

## 30、谈谈你对 keep-alive 的了解

```javascript
1、keep-alive 是 Vue 内置的一个组件，可以使被包含的组件保留状态，避免重新渲染
2、一般结合路由和动态组件一起使用，用于缓存组件
3、对应两个钩子函数 activated 和 deactivated ，当组件被激活时，触发钩子函数 activated，当组件被移除时，触发钩子函数 deactivated
4、提供 include 和 exclude 属性，两者都支持字符串或正则表达式， include 表示只有名称匹配的组件会被缓存，exclude 表示任何名称匹配的组件都不会被缓存 ，其中 exclude 的优先级比 include 高；
例如：
<keep-alive include="a">
 <component>
  <!-- name 为 a 的组件将被缓存！ -->
 </component>
</keep-alive>

<keep-alive exclude="a">
 <component>
  <!-- 除了 name 为 a 的组件都将被缓存！ -->
 </component>
</keep-alive>
```

<a name="B6CM2"></a>

## 31、vue中动态组件如何使用

```javascript
1、在某个中使用 is 特性来切换不同的组件：
	<component :is="TabComponent"></component>   TabComponent:已注册组件的名字
```

<a name="HjVgj"></a>

## 32、vue怎么实现强制刷新组件

```javascript
第一.使用this.$forceUpdate强制重新渲染
    <template>
    <button @click="reload()">刷新当前组件</button>
    </template>
    <script>
    export default {
        name: 'comp',
        methods: {
            reload() {
                this.$forceUpdate()
            }
        }
    }
    </script>

第二.使用v-if指令
<template>
    <comp v-if="update"></comp>
    <button @click="reload()">刷新comp组件</button>
</template>
<script>
import comp from '@/views/comp.vue'
export default {
    name: 'parentComp',
    data() {
        return {
            update: true
        }
    },
    methods: {
        reload() {
            // 移除组件
            this.update = false
            // 在组件移除后，重新渲染组件
            // this.$nextTick可实现在DOM 状态更新后，执行传入的方法。
            this.$nextTick(() => {
                this.update = true
            })
        }
    }
}
</script>
```

<a name="IYidu"></a>

## 33、如何在子组件中访问父组件的实例

```javascript
Vue中子组件调用父组件的方法，这里有三种方法提供参考：
    1：直接在子组件中通过this.$parent.event来调用父组件的方法
    2：在子组件里用$emit向父组件触发一个事件，父组件监听这个事件
    3：父组件把方法传入子组件中，在子组件里直接调用这个方法
```

<a name="puiKG"></a>

# 五、Vuex

<a name="Le3BR"></a>

## 34、Vuex 是什么？有哪几种属性？

```javascript
  1、Vuex 是专为Vue设计的状态管理工具，采用集中式储存管理 Vue 中所有组件的状态。
  2、属性
  （1）state属性：基本数据
  （2）getters属性：从 state 中派生出的数据
  （3）mutation属性：更新 store 中数据的唯一途径，其接收一个以 state 为第一参数的回调函数
  （4）action 属性：提交 mutation 以更改 state，其中可以包含异步操作，数据请求
  （5）module 属性：用于将 store分割成不同的模块。
```

<a name="wV6aw"></a>

## 35、vuex的出现解决了什么问题？

主要解决了以下两个问题: <br />1, 大面积的数据共享，解决了多个组件共用一份数据的问题。 <br />2, 多个组件都需要修改同一份数据，变得非常容易维护。 
<a name="DTWrQ"></a>

## 36、vuex的mutation和action之间的区别是什么？

Mutation:专注于修改 State，理论上是修改 State 的唯一途径，里面只能放同步代码<br />Action:放业务代码、异步请求，不能直接操作 State，需要调用 mutation 操作State。
<a name="mgv2H"></a>

## 37、刷新浏览器后，vuex的数据是否存在？如何解决？

刷新后，vuex的数据肯定不存在了，因为 store 里的数据是保存在运行内存中的，当页面刷新时，页面会重新加载vue实例，store里面的数据就会被重新初始化。<br />可以通过插件（[vuex-along](https://www.npmjs.com/package/vuex-along) 或 [vuex-persist](https://www.npmjs.com/package/vuex-persist#usage)）将store中的数据存储到localStorage里面。

- 当store里的数据更新后，插件会将数据更新到localStorage里面
- 页面刷新后，插件会将 localStorage 里的数据恢复到 store 中
  <a name="SRKR9"></a>

# 六、概念、原理

<a name="fBBtX"></a>

## 38、怎么理解vue中的虚拟DOM

```javascript
原理：	
	用 JS 对象模拟真实 DOM 树，对真实 DOM 进行抽象；
diff 算法 — 比较两棵虚拟 DOM 树的差异；
pach 算法 — 将两个虚拟 DOM 对象的差异应用到真正的 DOM 树。

好处：
	1、性能优化
    2、无需手动操作DOM
    3、可以跨平台，服务端渲染等
```

<a name="VqNYh"></a>

## 39、说说你对SPA单页面的理解。

SPA，就是单页 Web 应用 ，也就是说项目只有一个页面，所有的操作都在一个页面中完成。<br />SPA 的优缺点:<br />1)优点: 				 					

1.  无刷新界面，给用户体验原生的应用感觉  						
2.  节省原生开发成本，提高发布效率（无需每次安装更新包）。  					
3.  容易借助其他知名平台营销和推广  						
4.  符合 web2.0 的趋势  						

2)缺点:<br />1、性能和用原生JS开发的项目有一定差距<br /> 2、各个浏览器的版本兼容性不一样<br /> 3、业务随着代码量增加而增加，不利于首屏优化，不利于搜索引擎抓取<br />4、某些平台对 hash 有偏见
<a name="zhkqt"></a>

## 40、怎么理解vue的单向数据流？

数据从父级组件传递给子组件，只能单向绑定。

- 父级组件数据更新时，子组件中所有的 prop 都将会刷新为最新的值
- 子组件内部不能直接修改从父级传递过来的数据，如果想修改，只能通过 $emit 派发一个自定义事件，父组件接收到后，由父组件修改 
  <a name="WDlAl"></a>

## 41、怎么理解mvvm这种设计模式

```javascript
Model–View–ViewModel （MVVM） 是一个软件架构设计模式，是一种简化用户界面的事件驱动编程方式。
MVVM
    M Model 模型 指的是数据层
    V View  视图 指的是用户页面
    VM ViewModel 视图模型
    视图模型(VM)是MVVM模式的核心，它是连接view和model的桥梁，
      - 当model的属性改变时，VM会监听数据的变化，并更新view
      - 反之，当view变化后，VM也会将数据更新到model层。（我们称之为数据的双向绑定）
```

<a name="XaNIN"></a>

## 42、mvvm 和 mvc 区别是什么?哪些场景适合?	

MVC 和 MVVM 二者都是设计思想。主要区别是 MVC 中的 C（Controller） 演变成 MVVM 中的 VM（viewModel）

- MVVM 中的数据和视图是双向绑定的
- MVC中没有双向绑定的概念，需要通过 DOM 操作，来渲染数据和获取数据。

所以，数据操作比较多的场景，需要大量操作 DOM 元素时，采用 MVVM 的开发方式，会更加便捷，让开发者更多的精力放在数据的变化上，避免繁琐的 DOM 操作。
<a name="iZeFW"></a>

## 43、组件化和模块化的区别

```javascript
1、组件相当于库，把一些能在项目里或者不同类型项目中可复用的代码进行工具性的封装。
2、模块相应于业务逻辑模块，把同一类型项目里的功能逻辑进行进行需求性的封装。
```

<a name="DACze"></a>

## 44、你认为vue的核心是什么

```javascript
组件化
双向数据绑定
```

<a name="KOnNh"></a>

## 45、说说vue的优缺点

```javascript
优点：
    1.中文文档，方便学习
    2. 组件化开发，可以复用结构
    3. 双向数据绑定
    4. 单页面应用配合路由，切换路由时，页面局部刷新，加快访问速度和用户体验。
    5. 有很多第三方的 UI 组件库，比如 element、vant等等，开发方便
缺点：
    1.不支持IE8及以下浏览器
    2.吃内存（每个组件都会实例化一个Vue实例，实例的属性和方法很多）
    3.定义在data里面的对象，实例化时，都会递归的遍历转成响应式数据，然而有的响应式数据我们并不会用到，造成性能上的浪费
```

<a name="KxXkb"></a>

## 46、vue响应式的原理

```javascript
1、原理：
	Vue 的响应式原理是核心是通过 ES5 的 Object.defindeProperty 进行数据劫持，然后利用 get 和 set 方法进行获取和设置，data 中声明的属性都被添加到了get和set中，当读取 data 中的数据时自动调用 get 方法，当修改 data 中的数据时，自动调用 set 方法，检测到数据的变化，会通知观察者 Wacher，观察者 Wacher自动触发重新render 当前组件（子组件不会重新渲染）,生成新的虚拟 DOM 树，Vue 框架会遍历并对比新虚拟 DOM 树和旧虚拟 DOM 树中每个节点的差别，并记录下来，最后，加载操作，将所有记录的不同点，局部修改到真实 DOM 树上。

2、底层代码实现：
	   let data = {
        name: "lis",
        age: 20,
        sex: "男"
    }
//  vue2.0实现  使用Object.defineProperty进行数据劫持
    for(let key in data){
        let temp = data[key]
        Object.defineProperty(data, data[key], {
            get(){
                return temp
            },
            set(value){
                temp = value
            }
        })
    }
// vue3.0实现 使用Proxy 进行数据的代理
    let newData = new Proxy(data, {
        get(target, key){
            return target[key]
        },
        set(target, key, value){
            target[key] = value
        }
    })
```

<a name="MgrZH"></a>

## 47、vue2.0和vue3.0响应式的区别

```javascript
1、Object.defineProperty 
  1) 用于监听对象的数据变化
  2) 无法监听数组变化(下标，长度)
  3) 只能劫持对象的自身属性，动态添加的劫持不到
2、Proxy
  1) proxy返回的是一个新对象， 可以通过操作返回的新的对象达到目的
  2）可以监听到数组变化，也可以监听到动态添加的数据
```

<a name="IWwqe"></a>

## 48、SSR了解吗

```javascript
1、SSR也就是服务端渲染，也就是将Vue在客户端把标签渲染成HTML的工作放在服务端完成，然后再把html直接返回给客户端。
2、SSR有着更好的SEO、并且首屏加载速度更快等优点。不过它也有一些缺点，比如我们的开发条件会受到限制，服务器端渲染只支持beforeCreate和created两个钩子，当我们需要一些外部扩展库时需要特殊处理，服务端渲染应用程序也需要处于Node.js的运行环境。还有就是服务器的压力比较大。
```

<a name="Oo406"></a>

## 49、你都做过哪些Vue的性能优化

```javascript
1、v-if和v-for不能连用
2、页面采用keep-alive缓存组件
3、合理使用v-if和v-show
4、key保证唯一
5、使用路由懒加载、异步组件、组件封装
6、防抖、节流
7、第三方模块按需导入
8、图片懒加载
9、精灵图的使用
10、代码压缩
```

<a name="eTqPK"></a>

## 50、怎么解决vue打包后静态资源图片失效的问题

```javascript
在vue-cli 需要在根目录下建一个vue.config.js 在里面配置publicPath即可
默认值为/，更改为./就好了
```











