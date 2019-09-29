#第六章  DOM

##6.1DOM的概述

6.1.1DOM的概念

DOM文档对象模型，DOM对象不仅仅是一个普通的内置对象，它还是一个巨大的API的核心对象，它将文档呈现在js面前，并赋予了js操作文档能力，

6.1.2  DOM和JavaScript的关系

一个web页面是一个文档,这文档可以在浏览器窗口或者作为html源代码显示出来.但上述两种情况都是同一个文档,DOM提供了对同一份文档的另一种表现,存储和操作的方式.DOM能够使用JavaScript脚本语言进行修改.


6.1.3DOM节点

加载HTML页面是，web浏览器生成一个树形结构，用来表示内部结构，DOM将这种结构理解为节点组成，根据W3C的HTML DOM标准，HTML文档找那个内容都是节点；

>整个文档是一个文档节点
>
>每个html元素是元素节点
>
>HTML元素内的文本是文本节点

>每个html属性都是属性节点   
> 
>注释也是节点，叫注释节点


6.1.4  DOM树

DOM树体现html页面的层级结构，而DOM树有DOM文档和DOM元素树两种，DOM元素树包含的只有元素节点，而DOM文档树则包含DOM文档中的所有内容

##6.2查找元素

6.2.1 getElementById 用id获取元素

getElementById()的方法，接收一个参数：获取元素的id，如果找不到相应的元素，则返回该元素的，否则返回null.

    //用变量接 在文档中   找  元素  用id 'd'
       var d=document.getElementById('d');

6.2.2用标签名获取元素
getElementByIdName（）可以获取该元素名称下所有的元素。返回一个伪数组，或者说是一个节点的列表

    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>

    </ul>
    <script>
        var lis =document.getElementByIdName('li');
        //伪数组
         console.log(lis);
    </script>

在某一个元素中，并不是在全局文档中利用标签获取元素，这样更加精准

        var ul = document.getElementById('ul');
        var list = ul.getElementsByTagName('li');
        console.log(list);


6.2.3 用类名获取元素

		var a=document.getElementsByClassName('a');
         console.log(a);


6.2.4 用选择器获取元素

querySelector()和querySelectorAll()可以依靠选择器找到元素,但是前者只能找到元素列表的第一个元素,而后者可以全部找到.注意,该方法性能没有直接利用标签寻找高.

        var ul = document.getElementById('ul')
        var x = document.querySelector('#div>div a');
        var lis = ul.querySelectorAll('li');
        console.log(lis);




##6.3获取元素其他信息


6.3.1获取元素名

当我们使用id获取元素的时候，元素的名称会和整个元素一起显示出来，如果想要拿到该元素的元素名，也就是标签名则需要用tagName属性。该属性只能获取不能设置

    var div =document.getElementById('mydiv');
    console.log(div.tagName);//DIV




6.3.2 获取元素节点里的内容
 
当获取元素之后，如果我们需要拿到元素中的内容，则需要用另一个方法得到，元素里的内容包括：文本或元素,需要用innderHTML元素

    <div id="mydiv">
        sdasda
    </div>
     <script>
        var div =document.getElementById('mydiv');
        console.log(div.innerHTML);
          div.innerHTML='你好'
     </script>

innerHTML属性可以获取标签内的属性，还可以设置标签内的内容




6.3.3获取元素节点中的文本	 
    
利用innerText属性获取的只能是文本节点,不能是其他,当然innerText属性除了获取,也可以设置元素中的文本. 
    
	var div = document.getElementById('mydiv');
	consol.log(div.innerText);

	div.innerText = 'hello';

6.3.4  获取元素的类名

利用className属性获取元素的类名,以字符串的形式返回.同时可以设置新的class类名,需要注意的是,返回值是一个字符串.

        var div = document.getElementById('mydiv');
        console.log(div.className);

如果更换其中一个类,则需要考虑该字符串中其他类是否应该一起设置.

        div.className = 'd a c';
        console.log(div.className);

6.2.5 用name属性值获取元素
getElementsByName()方法可以获取相同名称的name元素,返回一个伪数组对象.

        <input type="radio" name="sex" value="0">男 
        <input type="radio" name="sex" value="1">女
    
        var sex = document.getElementsByName('sex');
        console.log(sex);
 
6.3.6获取元素样式


style属性可以获取元素内联样式的所有属性,当然如果继续在style中找属性名如:background-color,就可以得到该属性的值,以字符串的形式返回.同时也可以设置该属性,从而达到增加或更改样式,需要注意的是,以js形式增加的样式的优先级大于css优先级.

    <style>
        div{
            width: 500px;
            height: 500px;
            background-color: red;
        }
    </style>
     </head>
     <body>
    <div style="background-color: blue"></div>
    <script>
     var div=document.getElementsByTagName('div')
     console.log(div[0].style.background);
    
    </script>

6.3.7 获取元素名
getAttribute（）可以获取元素的某个属性，要将属性名称放在括号里记得要用引号括起来，返回值就是字符串形式的属性值

    var div=document.getElementById('mydiv');
      var a=document.getElementsByName('a')
       console.log(div.getAttribute('class'))
       console.log(a[0].getAttribute('href'))

6.3.8设置元素属性

 