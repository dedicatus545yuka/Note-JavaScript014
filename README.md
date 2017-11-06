# Note-JavaScript014
something for BOM, 定时器
## BOM
### BOM是什么  
- BOM 的全称为 Browser Object Model，被译为 浏览器对象模型。BOM 提供了独立于 HTML 页面内容，而与浏览器相关的一系列对象。主要被用于管理浏览器窗口及与浏览器窗口之间通信等功能。
- BOM 由一系列对象构成，这些对象可以简单理解为是由各个浏览器所提供的。例如 Window 对象等。
- 值得注意的是: BOM 是 JavaScript 中唯一一个没有标准的。
#### BOM结构树
![](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/mEBS70iqiGH0yNf3iTr2aNurjogUlf57IDBrCFc.QW0!/m/dPMAAAAAAAAAnull&bo=0QSAAgAAAAADB3U!&rf=photolist&t=5)    
- 通过上述图示我们可以知道，DOM 树结构中的入口 Document 对象也是属于 BOM 内容的一部分。
- Window 对象是 BOM 结构中的最顶层的对象，其他对象都是以 Window 对象的属性形式出现。  
### Window 对象
> Window 对象表示当前浏览器窗口，是 BOM 中最顶层的对象。Window 对象的属性和方法应用于当前整个浏览器窗口。
#### window对象的属性
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>window对象</title>
</head>
<body>
<script>
    /*
        1. 在浏览器环境中Global对象就是window对象
           Global对象的属性和方法就是window对象的属性和方法
        2. 还提供了当前DOM中所有的事件类型
        3. 其他BOM对象都是window对象的属性
        4. window对象提供了属性和方法
        5. HTML5提供的部分新特性
     */
    console.log(window);

    // 1. 变量与属性的关系，函数与方法的关系
    /*var str = 'string';
    console.log(str);// 全局变量
    console.log(window.str);// window对象的属性

    /!*delete window.str;
    console.log(window.str);// undefined*!/

    delete str;// 报错

    function fn(){
        console.log('function');
    }
    fn();// 全局函数
    window.fn();// window对象的方法*/

    // 2. 获取窗口的宽度和高度
    console.log(window.innerWidth,window.innerHeight);
    console.log(window.outerWidth,window.outerHeight);

    // 3. self属性 -> 表示window对象本身
    console.log(window === window.self);

    // 4. 判断是否为顶级窗口
    console.log(window.top === window.self);// true
</script>
</body>
</html>
```
#### window对象的方法  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>window对象的方法</title>
    <style>
        body {
            margin: 0px;
            height: 2000px;
        }
    </style>
</head>
<body>
<button id="btn">打开</button>
<button id="btn2">移动</button>
<script>
    // 1. 提示框
    // window.alert('这是提示框');
    /*var result = window.confirm('你确认要退出吗?');
    alert(result);*/
    /*var result = window.prompt('请输入你的名字','这是默认内容');
    alert(result);*/

    // 2. 打开和关系窗口
    // window.open('01_window对象的属性.html');

    /*window.myself = 'this is function';

    var btn = document.getElementById('btn');
    btn.onclick = function(){
        window.open('01_window对象的属性.html');
        console.log(window.myself);
    }*/

    var btn2 = document.getElementById('btn2');
    btn2.onclick = function(){
        window.scrollTo(0,2000);
    }

</script>
</body>
</html>
```
![open()方法的实现原理图](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/LbWmtZKzkjsyirOVD1g9YAFQxWoizGrT7.aSH4eKxUw!/m/dD8BAAAAAAAAnull&bo=GwWAAgAAAAADB74!&rf=photolist&t=5) 

- Window.moveBy(deltaX, deltaY) : 根据指定的值，移动当前窗口。
- window.moveTo(x, y) : 将当前窗口移动到指定的坐标位置。
- window.scrollTo(x-coord,y-coord ) ： 将浏览器窗口滚动到指定坐标值。
- window.resizeBy(xDelta, yDelta) 
- window.resizeTo(aWidth, aHeight) 

> DOM Level 0 不属于任何标准. 在浏览器中运行可能会出错。  

- window.scrollBy(X, Y) : 在窗口中按指定的距离滚动文档。
> DOM Level 2 标准

#### Navigator对象    
> Navigator 对象表示当前浏览器，该对象包含了浏览器的信息。

1. 常用属性  
- appCodeName ：浏览器的代码名  
- appName ：浏览器的名称
- appVersion ：浏览器的平台和版本信息
- platform ：运行浏览器的操作系统平台
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>navigator对象</title>
</head>
<body>
<script>
    console.log('浏览器的代码名: ' + navigator.appCodeName);
    console.log('浏览器的名称: ' + navigator.appName);
    console.log('浏览器的平台和版本信息: ' + navigator.appVersion);
    console.log('运行浏览器的操作系统平台: ' + navigator.platform);

</script>
</body>
</html>
```
2. userAgent属性   
- Navigator 对象提供很多属性，可以来识别当前浏览器及操作系统信息。但绝大多数属性在目前浏览器中已经不再起作用了。而 Navigator 对象的 userAgent 属性依旧可以实现识别浏览器的功能。
- userAgent 属性返回由客户机发送服务器的 user-agent 头部的值。userAgent 属性是一个只读的字符串，声明了浏览器用于 HTTP 请求的用户代理头的值。
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>userAgent属性</title>
</head>
<body>
<script>
    /*
        * 火狐浏览器的内核 -> Gecko
        * Chrome/Safari -> AppleWebKit(like Gecko)
        * IE 8 -> Trident
        * IE 11 -> Trident(like Gecko)
        * 国产浏览器
          * QQ浏览器 -> 号称自主内核
          * 百度浏览器 -> 号称自主内核
          * 遨游浏览器 -> 号称自主内核
     */
    console.log(navigator.userAgent);

</script>
</body>
</html>
```
![各种浏览器产品的userAgent属性值](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/6URA8FDOK*uI95Y8rj2YB.3DDLHr6QGn.zKwXQ1i24I!/m/dPMAAAAAAAAAnull&bo=HAaAAgAAAAADB7o!&rf=photolist&t=5)    

> 通过userAgent属性获取用户当前使用的浏览器产品，提供相应的浏览器兼容解决方案

```js
var ua = navigator.userAgent;

if(/firefox/i.test(ua)){
    console.log('当前使用的是 Firefox 浏览器');
}else if(/chrome/i.test(ua)){
    console.log('当前使用的是 Chrome 浏览器');
}else if(/safari/i.test(ua)){
    console.log('当前使用的是 Safari 浏览器');
}else if(/msie/i.test(ua)){
    console.log('当前使用的是 IE 11 之前版本的浏览器');
}else if("ActiveXObject" in window){
    console.log('当前使用的是 IE 11 浏览器');
}
```
> 通过 userAgent 属性获取用户当前使用的操作系统信息   

```js
if (/windows/i.test(ua)){
    console.log('当前使用的是 Windows 操作系统');
}else if (/mac/i.test(ua)){
    console.log('当前使用的是 Mac 操作系统');
}else if (/android/i.test(ua)){
    console.log('当前使用的是 Android 操作系统');
}else if (/iphone/i.test(ua)){
    console.log('当前使用的是 iPhone 操作系统');
}
```
#### History对象
> History 对象包含用户在浏览器中访问过的 URL（网址）。  

1. length属性
- History 对象的 length 属性可以获取用户在浏览器中访问网址的数量。
```js
console.log('用户访问的网址数量为: ' + history.length);
```
- 但是并不能通过遍历来获取用户的行为数据 
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>history对象</title>
</head>
<body>
<a href="04_userAgent属性.html">链接</a>
<script>
    // 浏览器机制 -> 有效地保护用户的行为隐私
    var length = history.length;
    for (var i=0;i<length;i++){
        console.log(history[i]);// undefined
    }

</script>
</body>
</html>
```
2. 前进与后退
- History 对象还提供了以下方法实现浏览器前进和后退功能。具体方法如下:
    - forward(): 实现跳转下一个页面，作用和浏览器的前进按钮一样。
    - back(): 实现转跳到上一个页面，作用和浏览器的回退按钮一样。
    - go(): 实现跳转到指定的页面。如果为负数表示后退，如果为正数表示前进。
#### Location对象
> Location对象包含了浏览器的地址栏中的信息。该对象主要用于获取和设置地址。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>location对象</title>
</head>
<body>
<script>
    console.log(location.href);
    /*
        URL完整格式
        http://localhost:63342/code/06_location对象.html?username=zhangwuji#
        * http -> 网络协议 -> location.protocol属性
        * localhost/127.0.0.1 -> IP地址 -> location.hostname属性
        * 63342 -> 端口号 -> location.port属性
        * /code/06_location对象.html -> 路径 -> location.pathname属性
        * ?username=zhangwuji -> 请求数据 -> location.search属性
     */

    /*  location.assign()方法 -> 载入一个新的文档，作用和直接修改 location 相同
        location.reload()方法 -> 等价于 F5 功能 -> 刷新页面
        location.replace()方法 -> 用新的文档替换当前文档（不会生成历史记录，不能使用回退按钮回退）
     */

</script>
</body>
</html>
```
#### screen对象
> 主要是针对屏幕获取一些数据，具体用到可以查帮助文档    

### 定时器
- Window 对象提供了有关定时执行 JavaScript 代码逻辑的方法，具体方法如下:   
```js
setInterval(code,millisec,lang)
```
- code : 要调用的函数或要执行的代码
- millisec : 定时器的周期时间，以毫秒为单位
- lang : 可选，JavaScript
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>定时器</title>
</head>
<body>
<button id="start">开始</button>
<button id="stop">结束</button>
<div id="show"></div>
<script>
    var start = document.getElementById('start');
    var show = document.getElementById('show');
    var t;
    start.onclick = function(){
        // 获取当前的时间
        /*var d = new Date();
        show.innerHTML = d.getHours() + ':' + d.getMinutes() + ':' + d.getSeconds();*/
        showTime();
        /*
            setInterval(code,time)
            * 参数
              * code - 表示按照指定周期所执行的代码块
                * 最简单的实现方式就是回调函数
              * time - 表示指定周期，以毫秒为单位
            * 返回值 - 作为当前定时器的标识(ID)
            * 问题
              * 导致第一次执行时，会出现指定时间的延迟
         */
        t = setInterval(showTime,1000);
    }

    function showTime(){
        // 获取当前的时间
        var d = new Date();
        show.innerHTML = d.getHours() + ':' + d.getMinutes() + ':' + d.getSeconds();
    }

    var stop = document.getElementById('stop');
    stop.onclick = function(){
        /*
            clearInterval(id)
            * id - 表示setInterval()方法的返回值
            * 取消 setInterval() 方法实现的定时器
         */
        clearInterval(t);
    }

</script>
</body>
</html>
```




