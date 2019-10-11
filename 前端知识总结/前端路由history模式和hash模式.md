**路由概念**
  路由可以理解为根据不同的URL地址栏的编号，展现的页面内容也不相同。从程序员的角度看问题，实际上就是不同的URL地址关联的函数不同。路由主要经理两种发展阶段：前端路由和后端路由。
1. 前端路由：实质上的映射函数就是显示和隐藏不同的DOM组件，即访问不同的页面路径时，显示不同的页面组件，不会再重新访问后台服务。
2. 后端路由：服务器路由,后台根据不同的地址请求，渲染生成不同的页面地址，然后返回给页面。

****
前端路由的缺陷：在使用浏览器的前进，后退键时会重新发送请求，来获取数据，没有合理地利用缓存。不同于后端路由，页面的渲染是在服务端进行的。
****

**前端路由的两种实现方案**
* hash方法
* history方法

**hash方法**
1. 显示：在地址中，存在一个#符号，在html中，成为锚。比如https://www.srtian.com#me。其中#之后的值称为hash值，即location.hash值。
2. hash特性：
* URL中hash值只是客户端的一种状态，也就是说当向服务器端发出请求时，hash部分不会被发送。
* hash值的改变，都会在浏览器的访问历史中增加一个记录。因此我们能通过浏览器的回退、前进按钮控制hash的切换。
* 我们可以使用hashchange事件来监听hash的变化。
3. hash值变化的触发：
* 通过html元素a标签中的锚进行触发
* 直接通过对location.hash值进行赋值
4. 缺点：
* URL地址中带有#符号，不美观
* 地址栏中存在hash，导致元素a中的锚不能生效

**history方法**
1. history API分为两个部分:
* 切换：
切换历史状态包括back、forward、go
三个方法，对应浏览器的*前进，后退，跳转*操作。
```
history.go(2)      // 跳转
history.back()     // 后退
history.forward()  // 前进
```

* 修改：
修改历史状态包括pushState,replaceState两个方法,这两个方法接收三个参数:stateObj,title,url
```
history.pushState({color:'red'}, 'red', 'red')
history.back();
setTimeout(function(){
    history.forward();
 },0)
window.onpopstate = function(event){
     console.log(event.state)
     if(event.state && event.state.color === 'red'){
           document.body.style.color = 'red';
      }
}
```
通过pushstate把页面的状态保存在state对象中，当页面的url再变回这个url时，可以通过event.state取到这个state对象，从而可以对页面状态进行还原，这里的页面状态就是页面字体颜色，其实滚动条的位置，阅读进度，组件的开关的这些页面状态都可以存储到state的里面。

2. 缺点：history模式丢掉了难看的#符号，同时支持前进、后退、跳转，但它就怕刷新。因为刷新是需要请求后端的，URL地址是随时可变的。不像HASH模式，后台的刷新只请求#符号之前的地址。所以history模式是需要后台服务器的支持，防止请求不到资源时，返回的是前端程序员最不愿意看到的404.

3. vue后台nginx的配置
```
location / {
  try_files $uri $uri/ /index.html;
}
```

**问题解决**
1. 帮助中心的从问题页面切换到具体问题描述页面的时候，滚动条依然保持前一个页面的状态？
*解决方案*：参考vue-router里面的<<滚动行为>>章节中。

2. 分享页面中，通过微信分享之后，在IOS微信遮罩层里面点击用浏览器(safi)打开，会存在页面不刷新的情况。
*问题原因*：这是由于分享页面的前端路由采用的是hash方法，hash方法的请求只取决#之前的URL地址，而每次分享的URL地址是都一样的，则导致safi浏览器误认为此次分享与之前的请求是一样的，则不会重新在刷新请求，导致错误。
*解决方案*：第一种方法可以直接采用history路由方法，但此种方法修改范围相对比较广。第二种方法，则可以直接监听hashchange事件，重新加载页面。







