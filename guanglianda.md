1.jsonp 跨域请求  ：http://www.cnblogs.com/mahatmasmile/archive/2013/03/29/2989505.html

2.css中的优先级：http://www.cnblogs.com/xugang/archive/2010/09/24/1833760.html
    ~~多重样式（Multiple Styles）：如果外部样式、内部样式和内联样式同时应用于同一个元素，就是使多重样式的情况。
        一般情况下，优先级如下：
        （内联样式）Inline style>（内部样式）Internal style sheet >（外部样式）External style sheet 
        有个例外的情况，就是如果外部样式放在内部样式的后面，则外部样式将覆盖内部样式。
        <head>
            <style type="text/css">
              /* 内部样式 */
              h3{color:green;}
            </style>
            <!-- 外部样式 style.css -->
            <link rel="stylesheet" type="text/css" href="style.css"/>
            <!-- 设置：h3{color:blue;} -->
        </head>
        <body>
            <h3>测试！</h3>
        </body>
        
     ~~选择器的优先权
        * 内联样式表的权值最高 1000
        * ID 选择器的权值为 100
        * Class 类选择器的权值为 10
        * HTML 标签选择器的权值为 1
        利用选择器的权值进行计算比较，示例如下：
        <head>
        <meta charset="UTF-8">
        <title>Document</title>
        <style type="text/css">
            #redP p {
                /* 权值 = 100+1=101 */
                color:#F00;  /* 红色 */
            }
            #redP .red em {
                /* 权值 = 100+10+1=111 */
                color:#00F; /* 蓝色 */
            }
            #redP p span em {
                /* 权值 = 100+1+1+1=103 */
                color:#FF0;/*黄色*/
            }
        </style>
        </head>
        <body>
            <div id="redP">
                <p class="red">red
                    <span><em>em red</em></span>
                </p>
                <p>red</p>
            </div>
        </body>
        
    ~~CSS 优先级法则：
        A  选择器都有一个权值，权值越大越优先；
        B  当权值相等时，后出现的样式表设置要优于先出现的样式表设置；
        C  创作者的规则高于浏览者：即网页编写者设置的CSS 样式的优先权高于浏览器所设置的样式；
        D  继承的CSS 样式不如后来指定的CSS 样式；
        E  在同一组属性设置中标有“!important”规则的优先级最大；示例如下：
        <html>
          <head>
            <style type="text/css">
             #redP p{
                /*两个color属性在同一组*/
                color:#00f !important; /* 优先级最大 */
                color:#f00;
             }
            </style>
          </head>
          <body>
             <div id="redP">
               <p>color</p>
               <p>color</p>
             </div>
          </body>
        </html>
        
    ~~~用js追加的样式也是符合css优先级法则的；
    
    http://zhidao.baidu.com/link?url=SQ180yU59LDhFd8XUOKVH-_fKha_DPfKiTdNb5KlVMtmJ8A0CqUjR18sAOzwKFLHfMAoyyVAtiGlTBO4uw3vv_
    
    https://segmentfault.com/a/1190000000453851

3.requireJs

4.用css实现一个弹出框，大小不固定且居中；
    http://www.jb51.net/article/34951.htm
    
    http://bbs.csdn.net/topics/390749797

5.js中的继承：

### call() 与apply() | bind()

    [参考链接1](https://www.runoob.com/w3cnote/js-call-apply-bind.html)
    
    http://uule.iteye.com/blog/1158829
    
    http://blog.csdn.net/myhahaxiao/article/details/6952321
    
    http://zhidao.baidu.com/link?url=5T2XTRDFHiSdGfgrw6tY0bA2ES1jGuU
    5RQIJhbepFvbFa_pXcH9dVf_0FBfTedDE2q9GPxL-aklsAkLM7PO461Kv8eXyipOlWtUAimelbva


7.前端自动化：
    yeoman  bower  grunt
    yeoman的作用：在web项目的立项阶段，使用yeoman来生成项目的文件，代码结构；
    yeoman自动将最佳实践和工具整合进来，大大加速和方便了我们后续的开发；生成器角色
    
    bower是一个web的包管理器；
    
    yeoman把grunt应用于生成的项目中
    grunt：三个基本概念 Task，Target，Options
  
8.angularJs中的双向数据绑定是如何实现的:http://sentsin.com/web/779.html
    AngularJS在$scope变量中使用脏值检查来实现了数据双向绑定。
    和Ember.js数据双向绑定中动态设施setter和getter不同，脏治检查允许AngularJS监视那些存在或者不存在的变量。

9.闭包的优缺点：http://www.phpddt.com/dhtml/javascript-closure.html
    优点：
    （1）不增加额外的全局变量，
    （2）执行过程中所有变量都是在匿名函数内部。
    缺点：
    （1）由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题。
        在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。
        
    （2）闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，
        把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），
        这时一定要小心，不要随便改变父函数内部变量的值。
        <script>
            function f1() {
                var n = 999;
                nAdd = function () {
                    n += 1
                }
                function f2() {
                    alert(n);
                }
                return f2;
            }
            var result = f1();
            result(); // 999
            nAdd();
            result(); // 1000
        </script>
        在这段代码中，result实际上就是闭包f2函数。它一共运行了两次，第一次的值是999，第二次的值是1000。这证明了，
        函数f1中的局部变量n一直保存在内存中，并没有在f1调用后被自动清除。为什么会这样呢？
        原因就在于f1是f2的父函数，而f2被赋给了一个全局变量，这导致f2始终在内存中，而f2的存在依赖于f1，因此f1也始终在内存中，
        不会在调用结束后，被垃圾回收机制（garbage collection）回收。这段代码中另一个值得注意的地方，
        就是"nAdd=function(){n+=1}"这一行，首先在nAdd前面没有使用var关键字，因此nAdd是一个全局变量，而不是局部变量。
        其次，nAdd的值是一个匿名函数（anonymous function），而这个匿名函数本身也是一个闭包，所以nAdd相当于是一个setter，
        可以在函数外部对函数内部的局部变量进行操作。

    http://blog.sina.com.cn/s/blog_50197c290101f870.html
    
    闭包：
    http://www.jb51.net/article/24101.htm
    
    http://www.cnblogs.com/TomXu/archive/2011/12/31/2289423.html

    闭包的使用场景：http://www.cnblogs.com/star-studio/archive/2011/06/22/2086493.html
    1.使用闭包代替全局变量
    2.函数外或在其他函数中访问某一函数内部的参数
    3.在函数执行之前为要执行的函数提供具体参数
    4.在函数执行之前为函数提供只有在函数执行或引用时才能知道的具体参数
    5.为节点循环绑定click事件，在事件函数中使用当次循环的值或节点，而不是最后一次循环的值或节点
    6.暂停执行
    7.包装相关功能

    <input type='button' id='b1' value="b1"/>
    <input type='button' id='b2' value="b2"/> 
    <input type='button' id='b3' value="b3"/>
    上面3个button，功能一样——每当被点击，就alert出自己目前为止一共被点击了多少次； 
    那么这个记录点击次数的变量放在哪里？这3个button的功能完全一样，事件函数可以写成一个，
    但却需要分别设立变量来存储自己被点击了多少次，那么这个时候闭包的作用就来了：
    把他们的事件监听函数设置为同一个函数的闭包，这样一来3个button的点击次数就独立变化了，
    且没有全局变量产生； 
    function genCount(){  
        var i = 0;  
        return function(){  
            i++;  
            alert(i) ; 
        }  
    }  
    function genCount2(){  
        var i = 0;  
        return function(){  
            i++;  
            return i; 
        }  
    } 
    var a = genCount();  
    var b = genCount();  
    var c = genCount2();  
    document.getElementById("b1").addEventListener("click",function(){
        a();
    })
    document.getElementById("b2").onclick=function(){
        b();
    };
    document.getElementById("b3").onclick=function(){
        var _c=c();
        console.log(_c);
    };
    闭包示例1：
    function test(){
    var name="xxx ";
    return function(){
    return name;
    }
    }
    var getName=test();
    getName();
    
    闭包示例2：
    function say667() {
    // Local variable that ends up within closure
    var num = 666;
    var ttt= function() { alert(num); }
    num++;
    return ttt;
    }
    var sayAlert = say667();
    sayAlert();
    闭包的示例3：
    function a(){
    var i=0;
    function b(){
    alert(i);
    }
    return b;
    }
    var c = a();
    c();
    链式作用域
