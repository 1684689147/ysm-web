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

##6.2获取元素

6.2.1 用id获取元素  getElementById

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




##6.3获取和设置元素其他信息


####6.3.1获取元素名

当我们使用id获取元素的时候，元素的名称会和整个元素一起显示出来，如果想要拿到该元素的元素名，也就是标签名则需要用tagName属性。该属性只能获取不能设置

    var div =document.getElementById('mydiv');
    console.log(div.tagName);//DIV




####6.3.2 获取元素节点里的内容
 
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




####6.3.3获取元素节点中的文本	 
    
利用innerText属性获取的只能是文本节点,不能是其他,当然innerText属性除了获取,也可以设置元素中的文本. 
    
	var div = document.getElementById('mydiv');
	consol.log(div.innerText);

	div.innerText = 'hello';

####6.3.4  获取元素的类名

利用className属性获取元素的类名,以字符串的形式返回.同时可以设置新的class类名,需要注意的是,返回值是一个字符串.

        var div = document.getElementById('mydiv');
        console.log(div.className);

如果更换其中一个类,则需要考虑该字符串中其他类是否应该一起设置.

        div.className = 'd a c';
        console.log(div.className);
 
####6.3.5获取元素样式


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

####6.3.6  获取元素属性



#####6.2.4 用name属性值获取元素
getElementsByName()方法可以获取相同名称的name元素,返回一个伪数组对象.

        <input type="radio" name="sex" value="0">男 
        <input type="radio" name="sex" value="1">女
    
        var sex = document.getElementsByName('sex');
        console.log(sex);

####6.3.7  设置元素属性

   setAttribute（）可以设置元素的某个属性，第一个参数是属性名，第二个参数是属性值都需要用引号括起来以逗号分隔


    var div =document.getElementsByTagName('div');
    var a=document.getElementsByTagName('a');
    div[0].setAttribute('id' ,'mydiv');
    a[0].setAttribute('href','http://www.baidu.com');


####6.3.8  删除元素属性、
使用   removeAttribute ，可以删除某个元素的某个属性，括号中放入需要删除的属性名用引号包裹

      var div=document.getElementById('mydiv')
      div.removeAttribute('id')
  

###6.4  增加元素

####6.4.1创建元素节点
  
利用js创建一个元素的方法是，现在一个文档中创建一个标签document.createElement()括号中写标签名,当然要用字符串形式.创建之后不是就存在了,而是需要这个已经创建的元素放到你想放到的元素(父级元素)中去.


            //用一个变量承接在文档中创建一个div元素
			var div = document.createElement("div");
			//将已经创建的元素放在想放的位置;
			document.body.appendChild(div);


####6.5.2 创建文本节点

利用js创建的文本节点,现在文档中创建文本。     
document.createTextNode('一段文字')在括号中将要创建的字符串放入,最后插入到需要的元素中.
		
	var p = document.getElementById("p");
	var text = document.createTextNode("一段文字");
	p.appendChild(text);


####6.4.3  css样式赋予

style.cssText是一个css的样式集合,他可以把css层叠样式表中的css样式直接放在该属性后,就不需要一条一条去赋予样式了,可以一次性赋予样式.
     
         div.style.cssText=
              'width:100px;height:100px;background-color:blue;'

#####6.4.4 在某元素前,插入创建的新元素.
insertBefore()这个函数和appendChild()用法基本一致,都是向父级中插入一个子元素,但是区别是,insertBefore是可以选择插入的位置,它需要插入到某一个子元素之前的位置,因此需要那个子元素,insertBefore()有两个参数,第一个参数是需要插入两个元素,第二个参数是在谁之前插入,两个参数用逗号分隔

	<ul id="ul">
			<li id="pg">苹果</li>
			<li id="jz">橘子</li>
			<li>香蕉</li>
	</ul>
	<script type="text/javascript">
		var ul = document.getElementById("ul");
		//获取苹果
		var pg = document.getElementById("pg");
		//插入li标签
		var li = document.createElement("li");
		//在父级中插入一个元素(插入元素,在谁前面)
		ul.insertBefore(li,pg);
		var t = document.createTextNode("火龙果");
		li.appendChild(t);
	</script>


###6.5删除和替换元素

####6.5.1元素的替换
 
元素的替换是在父元素中的一个子元素需要被另一个新元素所替代，使用replaceChild() 方法，该方法有两个参数第一个参数将要替换的新元素，第二个是被替换的旧元素中间用逗号隔开


       var div=document.getElementById('mydiv')
       var myp=document.createElement('p')
       document.body.replaceChild(myp,mydiv)
       //在父元素中替换子元素。第一个是新元素。第二个是旧的



####6.5.2  删除节点

元素的删除是在氟元素的其中一个子元素需要删除，使用removeChild()方法，将需要删除的元素放入括号中，
     var div=document.getElementById('mydiv')
          
            document.body.removeChild(div)


###6.6查找节点（node)
节点是在dom树上的每一个节点，其中包括：元素 文本  属性  注释等等。常用的有三个：元素 文本  属性 
          
####6.6.1节点的属性



      var div=document.getElementById('mydiv')
             console.log(div.nodeName);
             console.log(div.nodeValue;
             console.log(div.nodeType);


####6.6.2层次节点

节点可以分为父节点,与子节点、兄弟节点,当我们知道其中之一的时候，可以用一些方法找到另一个。

####6.6.3获取所有子节点
  
使用childNodes 实行拿到的是该属性的所有节点，包含所有几点类型，不单单只有元素



      <ul id="myul"><li>111</li><li>222</li><li>333</li> </ul>
    <script>
       var myul = document.getElementById('myul');
       /ildNodes是所有几点
       console.log(myul.childNodes);
    
    </script>

####6.6.4获取第一个和最后一个子节点
 
用 firstChild和lastChild可以拿到该元素下的第一个和最后一个子节点，注意不一定是元素节点
    
     <ul id="myul"><li>111</li><li>222</li><li>333</li> </ul>
        <script>
           var myul = document.getElementById('myul');
        
           console.log(myul.firstChild);
           console.log(myul.lastChild);

        
        </script>


#### 6.6.5获取父节点

使用parentNode可以拿到该元素的父节点,注意父节点只有一个.

    	<body>
		<ul id="myul"><li>111</li><li>222</li><li>333</li></ul>
		<script type="text/javascript">
			var myul = document.getElementById("myul");
			console.log(myul.parentNode);
		</script>
	</body>

####6.6获取兄弟节点 

可以previousSibling和nextSibling获得该元素的前一个和后一个兄弟节点，只能获取一个

             var mydiv = document.getElementById("mydiv");
              console.log(mydiv.previousSibling);
               console.log(mydiv.nextSibling);


###6.7  元素的宽高属性


#####6.7.1  offsetWidth和offseHeight属性


需要获取一个元素的宽度和高度，使用style是无法获取的，所以我们选着使用offsetWidth和offseHeight属性，该属性可以获取元素的站位宽高，它包含了内边距和边框


    var div=document.getElementById('mydiv')
     console.log(div.style);//这种方法只能拿到内联样式
     console.log(div.offsetWidth);


####6.7.2 clientWidth和clientHeight
clientWidth和clientHeight属性也可以获取元素的宽高，但与offsetWidth不同的书不包含边框。

		console.log(mydiv.clientWidth);


###6.8 子元素与父元素的距离    （一定出）
offsetLefte和offsetTop是距离body左边界和上边界的距离,但如果该子元素使用了定位属性,则offsetLefte和offsetTop参照的就不再是body而是距离它最近的父级元素
	
	var erzi = document.getElementById("erzi");
	console.log(erzi.offsetLeft);
	console.log(erzi.offsetTop);






    