# interview

#### HTML篇

1. 你是如何理解HTML语义化的？
    1. Div+span+css能搞定的布局为什么还需要这么多HTML标签.
    2. 扩展ARIA:[无障碍互联网应用](https://developers.google.com/web/fundamentals/accessibility/semantics-aria?hl=zh-cn)
2. meta 标签相关
    1. meta viewport 有什么应用场景？
    2. meta 怎么来设置缓存相关的配置？
3. 在HTML5中新增了哪些能力, 或者是哪些标签？[阅读MDN文档](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/HTML5)
4. HTML5manifest 用来做什么的，或者是HTML5中如何实现应用缓存？
    1. manifest方案已被Service Workers替代, 自然需要了解一下SW技术和对应应用（PWA）
    2. 阅读MDN文档：[使用应用缓存, 让web离线运行](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Using_the_application_cache)
5. DOM跨域是什么意思？
6. HTML5提供了哪一些存储能力, 他们常见的应用场景是哪些？
    1. 举例：indexDB常用在即时通讯系统中保存聊天消息。
    2. 注意websql并不是html5标准中的一部分，只是引入了使用sql来操作客户端数据库的api
7. 有时候我们在使用input的时候会配合label一起用,这里label起什么作用？
```xml
<label for="cheese">Do you like cheese?</label>
<input type="checkbox" name="cheese" id="cheese">
```
8. 图片相关？
    1. 有了解过什么是响应式图片吗？[阅读MDN响应式图片](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)
    2. 扩展阅读：[为什么通常在发送埋点数据时使用的是1*1的gif图](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/87)
    3. 图片实现懒加载的原理是什么？
    4. img 的 title和alt分别是用来做什么的？
    5. 图片热区有了解过吗？
9. 有听过HTML的数据属性吗？[扩展阅读数据属性](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes)
10. 有使用过那一些HTML5标签或特性？
    1. canvas/svg相关：
        1. 有听过canvas污染吗, 简述一下？
        2. 都是绘图技术, svg和canvas有什么不相同的地方？[扩展阅读1](https://g2.antv.vision/zh/docs/manual/tutorial/renderer)[扩展阅读2](https://www.zhihu.com/question/19690014)
    2. websocket相关：
        1. 有听过或者用过webscoket吗, 在什么场景使用？
        2. 大致介绍几个你知道的能及时获取数据的解决方案？
#### CSS篇

1. 如何实现水平居中/垂直居中？# 垂直居中是重点
2. CSS选择器优先级是怎么样的, 你自己的理解？
3. rem和em计算方案分别是怎么样的？
4. 需要实现一个自适应布局, 会使用什么样的CSS方案？
    1. #提示：百分比/...
5. CSS3中的`@supports`你有使用过吗，会在什么场景中使用？
    1. #提示：比如在使用类似于跨端框架开发时解决ios的安全底部时会使用到
6. 你理解的盒模型([Box model](https://developer.mozilla.org/en-US/docs/CSS/box_model))是什么样的, 以及你知道什么时候会出现[外边距合并](https://developer.mozilla.org/zh-CN/docs/CSS/margin_collapsing)吗？
7. 怎么理解BFC？[阅读MDN](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context)
8. 有使用过Flex和Grid进行布局吗？
9. 为什么会出现浮动, 以及可以怎么解决他？
10. 自定义字体和自定义变量
11. 为什么我们通常把css放在头部？[扩展阅读](https://juejin.im/post/6844904009694707725)
12. 有什么好的方式可以实现0.5px的细线
```css
<style>
.line {
    position: relative;
}
.line:after {
    content: "";
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 1px;
    background-color: #000000;
    -webkit-transform: scaleY(.5);
    transform: scaleY(.5);
}
</style>
<div class="line"></div>
```
1. CSS link 与 @import 的区别
2. clip-path有了解过吗？
3. 有什么好的方法能实现剩余空间全部分配给另一个元素？
    1. 提示flex-grow是其中一种实现
4. 你知道哪些解决css样式冲突的方法？
#### JavaScript/TypeScript篇

1. js中有哪些数据类型?
2. 闭包相关？
    1. 聊一聊你对闭包的理解, 用来解决什么问题？
    2. 怎么让以下代码每次循环♻️取值正确呢？
```javascript
 for (var i = 0; i < 10; i++) {
    setTimeout(function () {
      console.log(i) //10个10
    }, 1000)
  }
```
c. 你认为闭包有哪些缺点？
d. 怎么创建一个私有变量？

1. Promise
    1. 聊一聊你对promise的认识, 以及你在哪些场景下会使用他？
    2. promise 有哪些常用的api, 作用是什么？
    3. promise 在eventloop中的执行过程是怎样的？
    4. async...await是什么？
2. 聊一聊apply call bind之间的关系, 有什么好的方式来兼容他们？
3. 聊一聊你是怎么来理解this的？
4. 听说过预编译吗（变量提升知识）？
5. 什么是原型和原型链, 有哪些应用？
6. JS中怎么来实现继承？
7. 讲一下防抖和节流是什么, 你的实现思路是怎样的？
8. 造成跨域的原因是什么, 有哪些处理方式？
9. 说一下哪些情况下会是不属于同源的？
10. 怎么实现一个深拷贝？
11. 数组怎么去重？
12. 0.1 + 0.2 为什么不等于 0.3？
13. 对于数组扁平化, 有什么好的方法？
14. 在一些H5这样的应用中, 怎么来分辨运行的环境（微信/安卓/还是pc）？
15. EventHub 有了解过吗, 用来解决什么问题？
16. 简述一下执行上下文和执行栈？
17. 有听说过柯里化（curry）吗？
18. 你怎么理解高阶函数？
19. 说一下怎么取出数组的交集和并集, 思路？
20. 怎么实现一个冒泡排序和插入排序，思路？
21. 聊一聊js的eventloop?[扩展阅读](https://www.ruanyifeng.com/blog/2014/10/event-loop.html)
22. JS怎么来监听url hash 和 history值的变化？#其实是路由的原理
23. web-worker在什么场景下会使用到？
24. 怎么设置一个对象的编辑权限, 比如怎么让一个对象的某个key不可更改
25. window.requestAnimationFrame 可以用来做什么？#需要进阶回答需要可能需要提及到, 浏览器大多显示频率是16.7ms的问题 [扩展阅读](https://zhuanlan.zhihu.com/p/145793042)
26. Blob，ArrayBuffer、File、FileReader和FormData之间有什么区别？
27. 模块化
    1. 你是怎么理解模块化？
    2. amd/cmd/commnjs/esmodule之间有哪一些区别呢？
28. 为什么有人说dom操作会很消耗性能呢？
    1. 基础一些回答提一些重绘/重排的东西...
    2. 进阶回答可以提及到浏览器线程通讯问题，js-dom引擎分离开的原因。
29. typescript 中 void 和 never 两种分别表示什么类型？
30. 你认为typescript有什么好处？
#### HTTP篇

1. HTTP常见的状态码有哪些，分别是代表什么？
2. 大致说一下restful api规范是怎么样的，简述 ？（如：什么情况下会使用get/post/put/patch/delete等）
3. 当发现请求303时，怎么来设置会重定向到新的页面？
4. 有了http为什么还需要使用https,两者有什么不同？
5. http的缓存策略是什么样的？
6. 缓存命中规则是怎么样的，或者说是怎么知道是需要使用缓存而不是请求服务端呢？[扩展阅读](https://www.cnblogs.com/chenqf/p/6386163.html)
7. 聊一聊你理解的http无状态？
8. 可以介绍一下200和304有什么区别吗？
#### nodejs篇

1. 你认为nodejs给前端行业带来来哪些好处？
2. nodejs的eventloop是一个怎样的流程？
3. 你使用过哪些node框架，聊一聊你理解的洋葱模型？
4. 为什么需要child-process?
5. 你知道有哪些工具是基于node来实现的吗？
6. npm install xx --save 和 npm install xx --save-dev 拉取依赖时, 多一个dev会有什么不同？
7. Json web token(jwt)认证大致流程是怎么样的？
#### 打包构建篇

1. webpack打包原理是什么？
2. 构建过程是怎么样的？
3. 使用过哪些loader和plugin插件？
4. loader和plugin在什么情况下使用, 他们有什么不同？
5. 当发现整个项目打包构建比较慢时, 有什么好的解决办法？
6. tree-shaking是什么, 他的原理是什么？
7. source-map为什么发布时需要将其关闭？
8. 文件指纹有什么用？
9. webpack热更新原理？[扩展阅读](https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/118)
10. 你理解的webpack和rollup有什么不同？
11. webpack打包过后文件体积很大怎么办？
12. require.context有使用过吗，可以用来做什么？
13. gzip有什么用, 一般会涉及到哪些配置？
#### 框架篇

1. 聊一聊你理解的虚拟dom？
2. diff算法是什么？
3. vue数据响应式实现原理？
4. vue/react 相对应的组件间通讯方案？
5. react事件合成是什么？
6. 路由基本实现原理是什么？
7. react，如何理解fiber架构？
8. react，使用过哪些hooks？
9. 你对flux架构有了解吗？
10. vue生命周期函数以及对应的数据变化？
11. react/vue在遍历的时候会提供一个唯一的key, 有什么作用？
12. computed和watch有什么区别？
13. vue中直接给数组复制, vue能监测到值的变化吗, 为什么？
14. 父组件怎么调用子组件的方法，子组件如何调用父组件的方法？
15. 介绍一下vuex？
16. vue-router路由有哪些模式，有什么不同？
17. v-model本质实现是什么样的？
18. vue nexttick有什么用途,原理是什么？
19. proxy和defineProperty有什么优缺点？
20. 你是怎么理解mvvm的？
21. 在vue-router中提供了一个addRoutes, 用来动态添加路由规则, 但是在刷新以后会跳转到404, 你有什么好的方案解决这个问题？
22. vue3有哪一些新特性, 在数据响应式上又有什么不同？
23. routr.beforeEach在哪些场景会使用到？
24. react useState是怎么来更新值的？
25. react setState 为什么有时候获取值不是最新的？
26. react 受控组件和非受控组件, 你是怎么理解的？
27. 为什么在写JSX的时候都要求第一个字母大写？
28. 为什么我们要写 super(props)[扩展阅读](https://overreacted.io/zh-hans/why-do-we-write-super-props/)
29. 列举几个你知道的数据流管理方案，说一下都有什么特点？
30. react中想要导入一个svg怎么办？
    1. 你可以直接将 SVG 作为组件导入，而不是将其作为文件加载。此功能仅在`react-scripts@2.0.0`及更高版本中可用
```javascript
import { ReactComponent as Logo } from './logo.svg'
const App = () => (
  <div>
    {/* Logo is an actual react component */}
    <Logo />
  </div>
)
```
1. useMemo和useCallback分别会在什么场景下进行使用？
2. useEffect怎么来模拟生命周期的？
3. hook规则中为什么说：“不要在循环/条件/嵌套函数中”调用hook？
4. react中可以使用扩展运算符将剩余参数传递给组件，那么在vue中怎么来实现这种效果呢？
5. react中pureComponent 和 component 分别会在什么情况下使用？
6. 聊一聊类组件中的bind(this)
7. 聊一聊ssr有什么优缺点?
8. 你是怎么理解副作用的？
9. 对time slice（时间分片）有了解吗？
#### git篇

1. 你知道哪些分支管理模型, 有了解过git-flow吗？
2. 有哪些常用的命令？
3. git整个提交流程是怎么样的？
4. git中的head是什么？
5. 为什么说在git中开一个分支是很便宜的,你是怎么理解分支的？
6. reset/revert两个命令有什么不同？
7. 如果你只想要某个分支的某一次或几次提交怎么办？
8. 可以删除master分支吗, 为什么？
9. git merge/rebase合并有什么不同？
10. git push origin master这句命令在做什么？
11. git clone/fetch/pull 三个命令有什么不同呢？
12. 一不小心使用了 git reset --hard，把记录删除了怎么办？
13. 在git中有哪些东西能确定（标记）一个分支，或者是切换分支？
14. git bisect这个命令是用来干什么的？

#### 其他篇

1. XSS和CSRF 在什么情况下会产生，我们怎么来防御？
2. 移动端300ms的问题怎么解决？
3. 从输入url按下回车到页面展示给用户发生了什么？
4. 聊一聊你理解的垃圾回收机制？
5. 你知道js和native之间怎么进行通讯的吗？
6. 如果要实现一个跨端的应用, 有了解大致有哪一些解决方案吗（或者是自己的思路）？
7. 假如现在浏览器已经拿到来需要渲染的html-css-js等一些文件来, 浏览器怎么将他渲染成页面的？
8. 大致介绍几个你知道的设计模式？
9. 怎么设计一个文件上传组件，一半需要考虑到哪些点？
10. 聊一聊你是怎么理解前端工程化这个概念的？

<br>

#### 场景篇

1. 统一登录国际化问题

    **场景**

    假设现在有一个场景是这样的, “我们现在公司内部有很多的业务系统, 所有系统的登录都是使用的中台团队提供的统一登录（用户登录成功是可以访问所有有权限的系统）, 并且这个统一登录也可以管控到业务系统的国际化; 

    > **辅助信息** <br><br>
    > 假设中台统一登录的地址为: www.middle-platform.com/login <br>
    > 登录成功后重定向到: www.xxx.com/app/home <br>
    > <br>
    > 这里只是为了说明, 统一登录和业务系统是不同源, 并且storage在跨域到情况下是不可以直接更新/获取的;

    **问题**

    那么现在的问题是, 怎么设计能让中台统一登录可以控制到业务系统的语言, 在业务系统中切换也能控制到中台统一登录的语言”;
    > 阐述你的一下你到思路

2. 移动端刘海屏和ios安全底部问题

    **场景**

    假设现在我是用`uni-app`或者其他跨端框架进行app开发, 但是我在开发调试到时候发现安卓和ios除了需要处理刘海屏, ios大部分机型居然还有一个安全底部的东西, 并且这玩意对我内容造成了遮挡, 甚至导致我的无法正常使用应用;

    **问题**

    对应上述提到的两个问题, 请说一下你的解决方案：
    - 怎么解决ios/android设备刘海屏的问题;
    - 怎么解决ios的安全底部对内容造成遮挡;
    > 提示：ios系统版本对安全底部对解决方案会有影响, 甚至会导致应用不可用

....
