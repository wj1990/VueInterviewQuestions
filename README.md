1.构建的 vue-cli 工程都到了哪些技术，它们的作用分别是什么？
---
  vue.js：vue-cli工程的核心，主要特点是 双向数据绑定 和 组件系统。  
  vue-router：vue官方推荐使用的路由框架。  
  vuex：专为 Vue.js 应用项目开发的状态管理器，主要用于维护vue组件间共用的一些 变量 和 方法。  
  axios（ 或者 fetch 、ajax ）：用于发起 GET 、或 POST 等 http请求，基于 Promise 设计。  
  vux等：一个专为vue设计的移动端UI组件库。  
  创建一个emit.js文件，用于vue事件机制的管理。  
  webpack：模块加载和vue-cli工程打包器。 
  
2.vue-cli 工程常用的 npm 命令有哪些？
----
下载 node_modules 资源包的命令                      --- npm install  
启动 vue-cli 开发环境的 npm 命令                    --- npm run dev  
vue-cli 生成 生产环境部署资源 的 npm命令：           --- npm run build  
用于查看 vue-cli 生产环境部署资源文件大小的 npm命令   --- npm run build --report  

3.vue-cli目录结构？
----
build 文件夹：用于存放 webpack 相关配置和脚本。开发中仅 偶尔使用 到此文件夹下 webpack.base.conf.js 用于配置 less、sass等css预编译库，或者配置一下 UI 库。  
config 文件夹：主要存放配置文件，用于区分开发环境、线上环境的不同。 常用到此文件夹下 config.js 配置开发环境的 端口号、是否开启热加载 或者 设置生产环境的静态资源相对路径、是否开启gzip压缩、npm run build 命令打包生成静态资源的名称和路径等。  
dist 文件夹：默认 npm run build 命令打包生成的静态资源文件，用于生产部署。  
node_modules：存放npm命令下载的开发环境和生产环境的依赖包。  
src: 存放项目源码及需要引用的资源文件。  
src下assets：存放项目中需要用到的资源文件，css、js、images等。  
src下componets：存放vue开发中一些公共组件：header.vue、footer.vue等。  
src下emit：自己配置的vue集中式事件管理机制。  
src下router：vue-router vue路由的配置文件。  
src下service：自己配置的vue请求后台接口方法。  
src下page：存在vue页面组件的文件夹。  
src下util：存放vue开发过程中一些公共的.js方法。  
src下vuex：存放 vuex 为vue专门开发的状态管理器。  
src下app.vue：使用标签<route-view></router-view>渲染整个工程的.vue组件。  
src下main.js：vue-cli工程的入口文件。  
index.html：设置项目的一些meta头信息和提供用于挂载 vue 节点。  
package.json：用于 node_modules资源部 和 启动、打包项目的 npm 命令管理。  

4.config文件夹 下 index.js 的对于工程 开发环境 和 生产环境 的配置？
----
build 对象下 对于 生产环境 的配置：  

index：配置打包后入口.html文件的名称以及文件夹名称  
assetsRoot：配置打包后生成的文件名称和路径  
assetsPublicPath：配置 打包后 .html 引用静态资源的路径，一般要设置成 "./"  
productionGzip：是否开发 gzip 压缩，以提升加载速度  

dev 对象下 对于 开发环境 的配置：  

port：设置端口号  
autoOpenBrowser：启动工程时，自动打开浏览器  
proxyTable：vue设置的代理，用以解决 跨域 问题    

5.请你详细介绍一些 package.json 里面的配置？
----
scripts：npm run xxx 命令调用node执行的 .js 文件    
dependencies：生产环境依赖包的名称和版本号，即这些 依赖包 都会打包进 生产环境的JS文件里面  
devDependencies：开发环境依赖包的名称和版本号，即这些 依赖包 只用于 代码开发 的时候，不会打包进 生产环境js文件 里面。  

6.对于Vue是一套渐进式框架的理解？
----
Vue的核心的功能，是一个视图模板引擎，但这不是说Vue就不能成为一个框架。如下图所示，这里包含了Vue的所有部件，在声明式渲染（视图模板引擎）的基础上，我们可以通过添加组件系统、客户端路由、大规模状态管理来构建一个完整的框架。更重要的是，这些功能相互独立，你可以在核心功能的基础上任意选用其他的部件，不一定要全部整合在一起。可以看到，所说的“渐进式”，其实就是Vue的使用方式，同时也体现了Vue的设计的理念。  

7.请说出vue几种常用的指令？
----
v-for  类似JS的遍历，用法为 v-for="item in items", items是数组，item为数组中的数组元素。    
v-on  用于监听指定元素的DOM事件，比如点击事件。 @click="say"  
v-bind 当表达式的值改变时，将其产生的连带影响，响应式地作用于 DOM  
v-model 在表单元素上创建双向数据绑定  

8.请问 v-if 和 v-show 有什么区别?
---
 相同点：v-if与v-show都可以动态控制dom元素显示隐藏  
 不同点：v-if显示隐藏是将dom元素整个添加或删除，而v-show隐藏则是为该元素添加css--display:none，dom元素还在。  

9.vue常用的修饰符？
----
.stop ---------@click.stop="doThis"  阻止点击事件冒泡等同于JavaScript中的event.stopPropagation()  
.prevent  -----v-on:submit.prevent="doThis prevent等同于JavaScript的event.preventDefault()，用于取消默认事件  
.capture  ---- @click.capture="inner"  事件捕获由外到内,捕获事件  点击节点，就会触发从外至内的点击事件  
.self   ----- v-on:click.self="doThat"   
.once  ------@click.once="doThis"  点击按钮只会执行一次
.self.prevent -----v-on:click.self.prevent="doThis" 只会阻止对元素自身的点击  
.prevent.self -----v-on:click.prevent.self="doThis" 会阻止所有的点击  

.enter：回车键  ----- v-on:keyup.enter="submit"  
.tab：制表键    
.delete：含delete和backspace键    
.esc：返回键    
.space: 空格键   
.up：向上键    
.down：向下键    
.left：向左键    
.right：向右键   

.ctrl  -- @click.ctrl="doSomething"  
.alt  
.shift  
.meta  

.lazy ----v-model.lazy="msg" 光标离开input输入框的时候值才会改变  
.number --v-model.number="msg" 字符串转为Number类型  
.trim   -- v-model.trim="msg"  自动过滤用户输入的首尾空格  

10.v-on可以监听多个方法吗？
---
可以 v-on='{click:DoSomething,mouseleave:MouseLeave}'  

11.vue中 key 值的作用？
----
key来给每个节点做一个唯一标识，Diff算法就可以正确的识别此节点，找到正确的位置区插入新的节点。  
key的作用主要是为了高效的更新虚拟DOM，如果不添加key就会干掉原来已经渲染好的节点，重新渲染，导致效率低，有了key只需要更新位置即可。    

12.vue事件中如何使用event对象？
----
v-on:click="click($event, 233)"  

13.$nextTick的使用？
----
在数据变化后要执行的某个操作，而这个操作需要使用随数据改变而改变的DOM结构的时候，这个操作都应该放进Vue.nextTick()的回调函数中。
axios.get('.data.json').then((response) =>{  this.$nextTick(() => { this.getDoms() })  })  

14.Vue 组件中 data 为什么必须是函数?
----
var Vue = function() {}  
Vue.prototype.data = {  
  a: 1,  
  b: 2,  
}  
// 上面是一个虚拟的组件构造器，真实的组件构造器方法很多  
var componentA = new Vue()  
var componentB = new Vue()  
// 上面实例化出来两个组件实例  
componentA.data.a === componentB.data.a // true  
componentA.data.b = 5  
componentB.data.b // 5  
两个实例同时引用一个对象，那么当你修改其中一个属性的时候，另外一个实例也会跟着改 (对象的相互引用)
Vue.prototype.data = function() {  
  return {  
    a: 1,  
    b: 2,  
  }  
}    
每一个实例的data属性都是独立的

15.v-for 与 v-if 的优先级?
----
v-for比v-if优先，如果每一次都需要遍历整个数组，将会影响速度，尤其是当之需要渲染很小一部分的时候.  
  
16.vue中子组件调用父组件的方法?
----
（1） 
父组件 ----<child @fatherMethod="fatherMethod"></child>  
子组件 ---- this.$emit('fatherMethod');  
（2）  
父组件方法通过props传给子组件 然后子组件接受 调用  
（3）  
this.$parent.fatherMethod();  

17.vue中 keep-alive 组件的作用?
----
在vue项目中,难免会有列表页面,点击某个结果之后,返回回来时,如果不对结果页面进行缓存,那么返回列表页面的时候会回到初始状态,但是我们想要的结果是返回时这个页面还是之前搜索的结果列表,这时候就需要用到vue的keep-alive技术。  

<keep-alive>  
  <component>  
    <!-- 该组件将被缓存！ -->  
  </component>  
</keep-alive>  

include - 字符串或正则表达，只有匹配的组件会被缓存  
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

<keep-alive>  
    <router-view>  
        <!-- 所有路径匹配到的视图组件都会被缓存！ -->
    </router-view>  
</keep-alive>  

{  
    path: '/',    
    name: 'home',  
    component: Home,  
    meta: {  
      keepAlive: true // 需要被缓存  
    }  
}  

<keep-alive>  
    <router-view v-if="$route.meta.keepAlive">  
        <!-- 这里是会被缓存的视图组件，比如 Home！ -->  
    </router-view>  
</keep-alive>  

18.vue中编写可复用的组件？
----  
高内聚：从功能角度来度量模块内的联系，一个好的内聚模块应当恰好做一件事。它描述的是模块内的功能联系；  
低耦合：耦合组件之间关联程度的一种度量，低耦合即做到模块之间关联不大；

1.规范化命名：组件的命名应该跟业务无关，而是依据组件的功能命名。  
2.数据扁平化：定义组件接口时，尽量不要将整个对象作为一个 prop 传进来。每个 prop 应该是一个简单类型的数据。这样做有下列几点好处：  
   (1) 组件接口清晰。(2) props 校验方便。(3) 当服务端返回的对象中的 key 名称与组件接口不一样时，不需要重新构造一个对象。  
扁平化的 props 能让我们更直观地理解组件的接口。  
3.可复用组件只实现 UI 相关的功能，即展示、交互、动画，如何获取数据跟它无关，因此不要在组件内部去获取数据。  
4.可复用组件应尽量减少对外部条件的依赖。 
5.组件在功能独立的前提下应该尽量简单，越简单的组件可复用性越强。  
6.组件应具有一定的容错性。  

19.vue生命周期?
---
beforeCreate: new Vue()   data:undefined  el:undefined  
created: data存在 el:undefined 编译模板为虚拟dom放入到render函数中
beforeMount： data存在 el存在  
mounted ：完成挂载  
beforeUpdate: 更新之前 数据更新时调用，发生在虚拟 DOM 重新渲染之前 
updated:更新之后  
beforeDestroy:销毁之前  
destroyed:销毁之后  

20.vue如何监听键盘事件中的按键？
----
@keyup.13="submit"  
@keyup.enter="submit"  
 .enter  
 .tab  
 .delete (捕获“删除”和“退格”键)  
 .esc  
 .space  
 .up  
 .down  
 .left  
 .right  
 
 修饰键：    

 .ctrl  
 .alt  
 .shift  
 .meta  
按下Alt + 释放C触发  
@keyup.alt.67="clear"  

对于elementUI的input，我们需要在后面加上.native, 因为elementUI对input进行了封装，原生的事件不起作用。    
el-input v-model="form.name" placeholder="昵称" @keyup.enter.native="submit"  

21.vue更新数组时触发视图更新的方法（更新对象同理）？
----
Vue.set(target,key,value)
target: 对象或者数组 
key: string|数字 
(1)
this.$set(array, indexOfItem, newValue) 
(2)
this.$delete(target,key)
target: 对象或者数组
key: string|数字 
this.$delete(array, indexOfItem) 
(3)
this.array.splice(index, 1)

22.解决非工程化项目初始化页面闪动问题？
----
[v-cloak] {  display: none; }    
div id="app" v-cloak 

23.v-model语法糖的使用?
----
input type="checkbox" v-bind:checked="checked"  
checked数据修改了，那么DOM属性就会修改;   
如果DOM属性修改了，checked数据并不会修改;    

解决：  
 input type="checkbox" v-bind:checked="checked" @change="change"  ref="dom"  

change(){  
    this.checked = this.$refs.dom.checked  
}  

总结：这样做也太麻烦了，鉴于双向绑定也比较常用的，因此vue引入了一个指令v-model,可以使用它简化此工作：  
input type="checkbox" v-model="checked"  

24.单页面应用优缺点?
---
优点：  
1、具有桌面应用的即时性、网站的可移植性和可访问性。  
2、用户体验好、快，内容的改变不需要重新加载整个页面。  
3、基于上面一点，SPA相对对服务器压力小。  
4、良好的前后端分离。SPA和RESTful架构一起使用，后端不再负责模板渲染、输出页面工作，web前端和各种移动终端地位对等，后端API通用化。  
5、同一套后端程序代码，不用修改就可以用于Web界面、手机、平板等多种客户端；  

缺点：    
1、不利于SEO。（如果你看中SEO，那就不应该在页面上使用JavaScript，你应该使用网站而不是Web应用）    
2、初次加载耗时相对增多。    
3、导航不可用，如果一定要导航需要自行实现前进、后退。   

25.vue提供的几种脚手架模板?
---
webpack：基于 webpack 和 vue-loader 的目录结构，而且支持热部署、代码检查、测试及 css 抽取。  
webpack-simple：基于 webpack 和 vue-loader 的目录结构。  
browerify：基于 Browerfiy 和 vueify(作用于 vue-loader 类似)的结构，支持热部署、代码检查及单元测试。  
browerify-simple：基于 Browerfiy 和 vueify 的结构。  
simple：单个引入 Vue.js 的 index.html 页面。  

26.vue-cli开发环境使用全局常量？
----
第一步，在 src 下新建 const 文件夹下 新建 const.js  
├── src  
│   ├── const  
│   │    ├── const.js  
│   │     
│   └── main.js  
└── ...  
第二步，如何在 const.js 文件下，设置常量  
export default {
    install(Vue,options){
        Vue.prototype.global = {
            title:'全局',
            isBack: true,
            isAdd:  false,
        }; 
    }
 }
第三步，在 main.js 下全局引入：  
//引入全局常量  
import constant from './const/const.js'  
Vue.use(constant);  
//通过js方式使用：  
this.global.title  
//或在 html 结构中使用  
{{global.title}}  

27.vue-cli生产环境使用全局常量?
---
第一步，在 static 下新建 config.js：  
├── 项目路径  
│   ├── static  
│   │___├── config.js  

第二步，在 config.js 里面设置全局变量：  
window.g = {  
    PUBLIC_IP  : "http://10.10.10.10:8080"  
}  

第三步，在 index.html 里面引入：  
<script type="text/javascript" src="./static/config.js"></script>  

第四步，在其他 .js 文件中即可使用：  
window.g.PUBLIC_IP  

第五步，打包后修改：  
通过 npm run build 命令打包后，此 config.js 文件会被打包到 dist/static文件夹下，  
此时如果需要修改 PUBLIC_IP，打开config.js即可修改，无需重新打包！  

28.vue弹窗后如何禁止滚动条滚动？
----
methods : {  
   //禁止滚动  
   stop(){  
        var mo=function(e){e.preventDefault();};  
        document.body.style.overflow='hidden';  
        document.addEventListener("touchmove",mo,false);//禁止页面滑动  
    },  
    //滑动限制取消  
    move(){  
        var mo=function(e){e.preventDefault();};
        document.body.style.overflow='';//出现滚动条  
        document.removeEventListener("touchmove",mo,false);  
    }  
}  

29.计算属性的缓存和方法调用的区别?
---
计算属性必须返回结果  
计算属性是基于它的依赖缓存的。一个计算属性所依赖的数据发生变化时，它才会重新取值。  
使用计算属性还是methods取决于是否需要缓存，当遍历大数组和做大量计算时，应当使用计算属性，除非你不希望得到缓存。  
计算属性是根据依赖自动执行的，methods需要事件调用。  

30.






























  
