#第四章 函数
### 4.1 函数的概念
在JavaScript中,函数实际是一个对象,每个函数都是Function类型的实例,并且与其他引用类型一样具有属性和方法.  
通过函数可以封装任意多条语句,而且可以在任何地方任何时候调用执行.
在ECMAscript中函数使用function关键字来声明,后面跟一组函数名和函数体.

### 4.2 函数的创建和调用
4.2.1 函数声明语句
以这种方式创建的函数,会把整个函数提升到该作用域的最顶端,那么,不论在该作用域下何处调用都可以执行.如果在该作用域下的其他作用域下调用也可以执行.
         //关键词   函数名(参数列表)
         function aname(){
           //执行语句
           alert(123);
         }
         //函数的调用
         aname(); 

4.2.2 变量匿名函数

         //变量名  关键词(参数列表)
         var a = function(){
           //执行语句
         }
         //函数调用
         a();

4.2.3 匿名函数自调用

         //匿名函数自调用
         (function(){
            //执行语句
         })();

4.2.4 函数声明语句和变量匿名函数创建区别
函数声明语句创建的函数,在该作用域下任何地方调用均可,但以变量创建的匿名函数则和正常变量赋值相同,需要在变量赋值后调用,否则报错.

        a();//3
        function a(){
            alert(3);
        }

        b();//b is not a function
        var b = function(){
           alert(4);
        }

4.2.5 函数不能重载
重载就是在程序中可以定义多个相同函数名,不同参数列表的函数,调用者不必区分每个函数的参数,执行时,程序根据传入的参数个数,自动判断选择哪一个函数执行.
JavaScript语法不支持重载.

### 4.3 函数的参数
在JavaScript中函数的关键词后面跟随的小括号,是参数(形参)列表,调用时,表达式的括号中传入实际参数,函数的参数在function内可以用arguments对象来获取.

形参和实参是一一对应的.都可以用arguments获取到实参的内容.

        function aaa(x,y,z){
             console.log(arguments[1]);
        }
        aaa('a','b','c');

### 4.4 this
this是JavaScript语言的一个关键字,他代表函数运行时,自动生成的一个内部对象,只能在函数内部使用.随着函数使用场合的不同,this的值会发生变化,但有一个原则,就是this指的是,调用函数的那个对象.
绑定事件,this代表指定调用函数的对象.

    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
    div {
        width: 50px;
        height: 50px;
        background-color: red;
        float: left;
        margin: 20px;
    }
    </style>
    </head>
    <body>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <script>
       var div=document.getElementsByTagName("div");
			 for(var i=0;i<div.length;i++){
          		div[i].onclick = function(){
                this.style.backgroundColor = 'blue';
         	   }
       		 }
    </script>
    </body>
    </html>

###函数的返回值

