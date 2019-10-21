1.将两个字符利用字符串对象的方法变成一个字符,显示在页面id为h1的元素中
答:
  <h1 id="h1"></h1>
    <script>
         var h1=document.getElementById('h1');
        var a=new String('你好');
        var b=new String('好');
        var c = a.concat(b);
         h1.innerHTML=c;



2.一个富豪想存87万,给理财顾问写了87w,请自动生成存储870000的方法,显示在页面id为h2的元素中
答: 
<h2 id="h"></h2>

    <script>
        var h=document.getElementById('h');
        var str='87';
			var estr=str.padEnd(6,'0')
            h.innerHTML=estr;
    </script>



3.一个数字79387.348的工程款,保留两位小数存入,显示在页面id为h3的元素中
答: 
   <h3 id="h"></h3>
    <script>
          var h=document.getElementById('h');
          var a=79387.348;
          var b= a.toFixd(2);
          h.innerHTML=b;



4.一张图片是一个相对路径img/head/,icon/1.jpg,我只需要拿到它的文件夹目录后显示在页面id为h4的元素中
答: 
<img src="img/head/icon/1.jpg" id="img"/>
		<h4 id="h"></h4>
		<script type="text/javascript">
			var img=document.getElementById("img");
			var h=document.getElementById("h");
			h4.innerHTML=img.src;




5.用户输入验证码,无论大小写输入都会正确的方法,显示在页面id为h1的元素中,显示在页面id为h4的元素中
答:
 
                <h5 id="h5"></h5>
                <script type="text/javascript">
                    var a = prompt("请输入验证码:ABC");
                    var num="Abc";
                    if(num.toLowerCase==a.toLowerCase||num.toUpperCase==a.toUpperCase){
                        alert("输入正确");
                    }
                    var h5=document.getElementById("h5");
                    h5.innerHTML=a;
                </script>


