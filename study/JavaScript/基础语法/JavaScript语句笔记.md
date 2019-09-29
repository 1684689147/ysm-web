#第五章  JavaScript语句

 ###5.1分支语句

5.1.1 if的语句

     var a=10;
     //小括号里一定是true
     if(a<20){
       alert('yes')
     }


     if(a<10){
       alert('yes')
     }else{
       alert('no')
    }

5.1.3  if ....else if语句

    if(a<60){
       alert('D')
     }else if(a>=60 &&a<75){
       alert('C')
     }else if(a>=75 &&a<85){
       alert('B')
     }else if(a>=85 &&a<100){
       alert('A')
     }else{
       alert('缺考')
     }

5.1.4  switch 语句

        var a = 10;
        //将判断的内容写在括号里
        switch(a){
            case 值1:
            //执行代码
            break;
            case 值2:
            //执行代码
            break;
            case 值3:
            //执行代码
            break;
            case 值n:
            //执行代码
            break;
            default:
            //执行代码
        }

switch小括号中一般情况是一个变量名,这个变量可能会有不同的取值.所有的case都是"或"的关系,case后面的值会与变量值作比对,满足后就执行case后面的代码.不写break就会将所有的比对进行一遍.