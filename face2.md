## 判断一个变量是否是数组？

    var arr = [1,2,3,4];

    
    第1种方法，!!arr.push 看看是否有push方法 如果有 就是数组

    console.log(!!arr.push)  
    
    第2种方法，把类型检测转化为字符串比较
    
    console.log(Object.prototype.toString.call(arr) 
    === '[object Array]') 
    
## javascript 的本地对象，内置对象和宿主对象?
            
    本地对象为 array obj regexp 等可以 new 实例化
    内置对象为 gload Math 等不可以实例化的
    宿主为浏览器自带的 document,window 等
    
## Javascript 创建对象的几种方式？

    <!--1、var obj = {};（使用 json 创建对象）-->
    <!--如：obj.name = '张三';-->
    <!--obj.action = function ()-->
    <!--{-->
    <!--alert('吃饭');-->
    <!--};-->
    
    <!--2、var obj = new Object();（使用 Object 创建对象）-->
    <!--如：obj.name = '张三';-->
    <!--obj.action = function ()-->
    <!--{-->
    <!--alert('吃饭');-->
    <!--};-->
    
    <!--3、通过函数创建对象。-->
    <!--(1)、使用 this 关键字-->
    <!--如：var obj = function (){-->
    <!--this.name ='张三';-->
    <!--this.age = 19;-->
    <!--this.action = function ()-->
    <!--{-->
    <!--alert('吃饭');-->
    <!--};-->
    <!--}-->
    <!--(2)、使用 prototype 关键字-->
    <!--如：function obj (){}-->
    <!-- obj.prototype.name ='张三';-->
    <!--obj.prototype.action=function ()-->
    <!--{-->
    <!--alert('吃饭');-->
    <!--};-->
    
    <!--4、通过 Window 创建对象。-->
    <!--如：window.name = ''张三';-->
    <!--window.age = 19;-->
    <!--window.action= function()-->
    <!--{-->
    <!--alert('吃饭');-->
    <!--};-->
    
    <!--5、使用内置对象创建对象。-->
    <!--如：var str = new String("实例初始化 String");-->
    <!--var str1 = "直接赋值的 String";-->
    <!--var func = new Function("x","alert(x)");//示例初始化 func-->
    <!--var obj = new Object();//示例初始化一个 Object-->
    1. 简单对象的创建，使用对象字面量的方式{}创建一个对象（最简单，好理解，推荐使用）
    var obj = {};
    2.new一个类的实例
    2.1有参构造函数
    2.2无参构造函数
       定义一个function，如果有new关键字去"实例化",那么该function可以看作是一个类
       一个是构造函数下有属性，这个实例化对象身上就有这些属性
       一个是构造函数下没继承的东西，可以在实例化对象上添加属性和方法
    3.使用工厂方式来创建（Object关键字）
    var person = new Object();
    4.使用原型对象的方式  prototype关键字
    在构造函数的原型下添加方法,通过原型链的查找，这个实例化对象也有这些属性和方法
    function Dog(){
    
    }
    Dog.prototype.name="旺财";
    Dog.prototype.eat=function(){
       alert(this.name+"是个吃货");
    }
    var wangcai =new Dog();
    wangcai.eat();

    

## eval 是做什么的？

    它的功能是把对应的字符串解析成 JS 代码并运行；
    
    应该避免使用 eval，不安全，非常耗性能（2 个步骤，
    一次解析成 js 语句，一次执行）
    
## JS中Null与Undefined的区别
    
    在JavaScript中存在这样两种原始类型:Null与Undefined。

    null
        表示尚未存在的对象
     undefined
        当声明的变量还未初始化时，默认值是undefined


    
## javascript 代码中的"use strict";是什么意思 ? 使用它区别是什么？

    意思是使用严格模式，使用严格模式，一些不规范的语法将不再支持

## 如何判断一个对象是否属于某个类？

    Instanceof   constructor
    
## Ajax 是什么? 如何创建一个 Ajax？

    Ajax 并不算是一种新的技术，全称是 asychronous javascript and xml，可以说是已有技术的组合，主要
    用来实现客户端与服务器端的异步通信效果，实现页面的局部刷新，早期的浏览器并不能原生支持 ajax，可以
    使用隐藏帧（iframe）方式变相实现异步效果，后来的浏览器提供了对 ajax 的原生支持
    使用 ajax 原生方式发送请求主要通过 XMLHttpRequest(标准浏览器)、ActiveXObject(IE 浏览器)对象实现
    异步通信效果
    
    AJAX 基本步骤：

        初始化ajax对象
        
        连接地址，准备数据
        
        发送请求
        
        接收数据（正在接收，尚未完成）
        
        接收数据完成
    
    基本步骤：
    var xhr =null;//创建对象
    if(window.XMLHttpRequest){
    xhr = new XMLHttpRequest();
    }else{
    xhr = new ActiveXObject("Microsoft.XMLHTTP");
    }
     xhr.open(“方式”,”地址”,”标志位”);//初始化请求
     xhr.setRequestHeader(“”,””);//设置 http 头信息
     xhr.onreadystatechange =function(){}//指定回调函数
     xhr.send();//发送请求
     
    js 框架（jQuery/EXTJS 等）提供的 ajax API 对原生的 ajax 进行了封装，熟悉了基础理论，再学习别的框
    架就会得心应手，好多都是换汤不换药的内容
    
    
##     如何解决跨域问题?
    理解跨域的概念：协议、域名、端口都相同才同域，否则都是跨域
    出于安全考虑，服务器不允许 ajax 跨域获取数据，但是可以跨域获取文件内容，所以基于这一点，可以动
    态创建 script 标签，使用标签的 src 属性访问 js 文件的形式获取 js 脚本，并且这个 js 脚本中的内容是函数调
    用，该函数调用的参数是服务器返回的数据，为了获取这里的参数数据，需要事先在页面中定义回调函数，在回
    调函数中处理服务器返回的数据，这就是解决跨域问题的主流解决方案

## 将字符串”<tr><td>{$id}</td><td>{$name}</td></tr>”中的{$id}替换成10，{$name}替换成 Tony （使用正则表达式）
    
    "<tr><td>{$id}</td><td>{$id}_{$name}</td></tr>".replace(/{\$id}/g, '10').replace(/{\$name}/g, 'Ton
    y');
    

    /*
    			jQuery版的
    			1.先引入那个jQ文件
    			2.
    */
    .ajax({
    	url:'php/get.php',
    	data:{
    		pname:$('#input').val()
    	},
    	success:{
    		$('span').text(data)
    		//这个data就是后台返回的数据
    	}
    })
    		
        get和post的区别：
        get:通过url来发送数据给后端
        	相对来说不安全
        	体积受浏览限制
        	不用设置请求头
        post:
        	通过send发送数据给后端
        	安全性好
        	体积不受浏览器限制
        	需要加请求头
    	
## 数组去重：var arr=[1,2,3,4,5,22,33,33,98,108,98];
	
    var n = [];
    for(var i=0;i<arr.length;i++){
    	//arr.indexOf返回第一次出现的数字下标
    	if(arr.indexOf(arr[i]) == i){
    		n.push(arr[i]);
    	}
    }
    console.log(n)
    
    
    
    
    
