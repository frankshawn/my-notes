#### 对HTML语义化的理解？
1. 用正确的标签做正确的事情
1. html语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析
1. 即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的
1. 搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO
1. 使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解

#### 如何修改chrome记住密码后自动填充表单的黄色背景？
```css
input:-webkit-autofill, textarea:-webkit-autofill, select:-webkit-autofill {
  background-color: rgb(250, 255, 189);
  background-image: none;
  color: rgb(0, 0, 0);
}
```

#### 让页面里的字体变清晰，变细用CSS怎么做？
```css
-webkit-font-smoothing: antialiased;
```

#### 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？
1. 详细版：
  1. 浏览器会开启一个线程来处理这个请求，对 URL 分析判断如果是 http 协议就按照 Web 方式来处理
  1. 调用浏览器内核中的对应方法，比如 WebView 中的 loadUrl 方法
  1. 通过DNS解析获取网址的IP地址，设置 UA 等信息发出第二个GET请求
  1. 进行HTTP协议会话，客户端发送报头(请求报头)
  1. 进入到web服务器上的 Web Server，如 Apache、Tomcat、Node.JS 等服务器
  1. 进入部署好的后端应用，如 PHP、Java、JavaScript、Python 等，找到对应的请求处理
  1. 处理结束回馈报头，此处如果浏览器访问过，缓存上有对应资源，会与服务器最后修改时间对比，一致则返回304
  1. 浏览器开始下载html文档(响应报头，状态码200)，同时使用缓存
  1. 文档树建立，根据标记请求所需指定MIME类型的文件（比如css、js）,同时设置了cookie
  1. 页面开始渲染DOM，JS根据DOM API操作DOM,执行事件绑定等，页面显示完成
1. 简洁版
  1. 浏览器根据请求的URL交给DNS域名解析，找到真实IP，向服务器发起请求
  1. 服务器交给后台处理完成后返回数据，浏览器接收文件（HTML、JS、CSS、图象等）
  1. 浏览器对加载到的资源（HTML、JS、CSS等）进行语法解析，建立相应的内部数据结构（如HTML的DOM）
  1. 载入解析到的资源文件，渲染页面，完成

#### `display: none;`与`visibility: hidden;`的区别
1. 相同点
  1. 它们都能让元素不可见
1. 不同点
  1. display:none;会让元素完全从渲染树中消失，渲染的时候不占据任何空间；visibility: hidden;不会让元素从渲染树消失，渲染师元素继续占据空间，只是内容不可见
  1. display: none;是非继承属性，子孙节点消失由于元素从渲染树消失造成，通过修改子孙节点属性无法显示；visibility: hidden;是继承属性，子孙节点消失由于继承了hidden，通过设置visibility: visible;可以让子孙节点显式
  1. 修改常规流中元素的display通常会造成文档重排。修改visibility属性只会造成本元素的重绘
  1. 读屏器不会读取display: none;元素内容；会读取visibility: hidden;元素内容

#### HTTP 请求的类型
1. GET是最常用的方法，通常用于请求服务器发送某个资源
1. HEAD与GET类似，但服务器在响应中值返回头部，不返回实体的主体部分
1. PUT让服务器用请求的主体部分来创建一个由所请求的URL命名的新文档，或者，如果那个URL已经存在的话，就用这个主体替代它
1. POST起初是用来向服务器输入数据的。实际上，通常会用它来支持HTML的表单。表单中填好的数据通常会被送给服务器，然后由服务器将其发送到要去的地方
1. TRACE会在目的服务器端发起一个环回诊断，最后一站的服务器会弹回一个TRACE响应并在响应主体中携带它收到的原始请求报文。TRACE方法主要用于诊断，用于验证请求是否如愿穿过了请求/响应链
1. OPTIONS方法请求web服务器告知其支持的各种功能。可以查询服务器支持哪些方法或者对某些特殊资源支持哪些方法
1. DELETE请求服务器删除请求URL指定的资源

#### PNG,GIF,JPG的区别及如何选
1. GIF
1. 8位像素，256色
  1. 无损压缩
  1. 支持简单动画
  1. 支持boolean透明
  1. 适合简单动画
1. JPEG
  1. 颜色限于256
  1. 有损压缩
  1. 可控制压缩质量
  1. 不支持透明
  1. 适合照片
1. PNG
  1. 有PNG8和truecolor PNG
  1. PNG8类似GIF颜色上限为256，文件小，支持alpha透明度，无动画
  1. 适合图标、背景、按钮

#### CSS有哪些继承属性
1. 关于文字排版的属性，如
  1. font
  1. word-break
  1. letter-spacing
  1. text-align
  1. text-rendering
  1. word-spacing
  1. white-space
  1. text-indent
  1. text-transform
  1. text-shadow
1. line-height
1. color
1. visibility
1. cursor

#### 用js实现千位分隔符?
参考：http://www.tuicool.com/articles/ArQZfui
```javascript
function commafy(num) {
    return num && num.toString().replace(/(\d)(?=(\d{3})+\.)/g, ($1, $2) => $2 + ',');
}

console.log(commafy(1111111111.23)) // 1,111,111,111.23
```



  polyfill 是“在旧版浏览器上复制标准 API 的 JavaScript 补充”,可以动态地加载 JavaScript 代码或库，在不支持这些标准 API 的浏览器中模拟它们。
  例如，geolocation（地理位置）polyfill 可以在 navigator 对象上添加全局的 geolocation 对象，还能添加 getCurrentPosition 函数以及“坐标”回调对象，
  所有这些都是 W3C 地理位置 API 定义的对象和函数。因为 polyfill 模拟标准 API，所以能够以一种面向所有浏览器未来的方式针对这些 API 进行开发，
  一旦对这些 API 的支持变成绝对大多数，则可以方便地去掉 polyfill，无需做任何额外工作。

  Object.is() 与原来的比较操作符“ ===”、“ ==”的区别？

  两等号判等，会在比较时进行类型转换；
  三等号判等(判断严格)，比较时不进行隐式类型转换,（类型不同则会返回false）；

  Object.is 在三等号判等的基础上特别处理了 NaN 、-0 和 +0 ，保证 -0 和 +0 不再相同，
  但 Object.is(NaN, NaN) 会返回 true.

  Object.is 应被认为有其特殊的用途，而不能用它认为它比其它的相等对比更宽松或严格。
