# JS语法基础  
## 一、JS组成  
1.ECMAScript:描述的是JavaScript的基础语法标准  
2.DOM(Document Object Model):文档对象模型  
3.BOM(Browser Object Model):浏览器对象模型  
## 二、变量  
### 1.含义:存储数据的容器，存放在这个容器里的数据，可以发生变化  
### 2.声明方式:var声明变量  
### 3.命名规范:  
①由数字、字母、下划线和$构成，并且不能以数字开头  
②驼峰命名法，如var wuJiaYi=“吴嘉怡”  
③不能和系统关键字以及系统保留字冲突，如var var=123不行  
④不能含有空格  
⑤区分大小写  
###  4.查看方式:用typeof查看  
###  5.作用域链:  
相同的变量名会产生一个作用域链，访问该变量名称的时候，会首先找奔曾是否有该变量，如果没有去父级找，最终找到全局变量为止，如果全局变量也没有，那么会报错  
###  6.全局变量和局部变量:  
全局变量:是在JS下声明的可以全程被调用到的变量  
局部变量:是在JS函数中声明的变量  
区别:全局变量可以全程被对象或函数调用，而局部变量存在闭包问题，外面调用不到函数内部的局部变量  
##  三、数据类型  
###  1.基本数据类型  
String字符串，Number数字，undefined未定义(变量只有声明，没有赋值)，Null空(变量声明了并且变量值为null)，Boolean布尔值(判断真假，true和false)  
###  String字符串(“ ”)  
###  声明方式:  
    var str=new String();
    str="wu";
        
    var str="wu";  
###  方法:  
(1)charAt( )，通过下标寻找字符串相应的位置  
	
	var str="i love you";
	var word=str.charAt(0);//下标从0开始寻找
	console.log(word);//i  
(2)toUpperCase( )，转化为大写字母

	var str="Hello WORLD!";
	var newstr=str.toUpperCase();
	console.log(newstr);//HELLO WORLD  
(3)toLowerCase( )，转化为小写字母

	var str="Hello WORLD!";
	var newstr=str.toLowerCase();
	console.log(newstr);//hello world  
(4)indexOf( )，获取指定字符内容第一次在字符串中出现的下标，没有返回-1:第一个参数表示找的内容；第二个参数表示从哪个下标开始找起

	var str="hello world hello lanou";
	var index=str.indexOf("hello");
	console.log(index);//0
	
	var str="hello world hello lanou";
	var index=str.indexOf("hello",3);
	console.log(index);//12
	
	var index=str.indexOf("x");
	console.log(index);//-1  
(5)lastIndexOf( )，获取指定字符最后一次出现在字符串中的下标

	var str="hello world hello lanou";
	var index=str.lastIndexOf("hello");
	console.log(index);//12  
(6)charCodeAt( )，通过下标返回相应位置对应字符的Unicode编码

	var str="hello world";
	var num=str.charAt(1);
	var num2=str.charCodeAt(1)
	console.log(num,num2);//e 101  
(7)search( )，查找，如果找得到，返回下标，找不到返回-1

	var str="hello world";
	var res=str.search("llo");
	console.log(res);//2
	
	var res=str.search("a");
	console.log(res);//-1  
(8)concat( )，连接一个或多个字符串

	var str="乖乖";
	var str2=str.concat("你好","!");
	console.log(str2);//乖乖你好！  
(9)replace( )，替换，后者代替前者，只能出现一次

	var str="hello world";
	var newstr=str.replace("world","lanou");
	console.log(newstr);//hello lanou  
(10)截取方式:  
slice( )，对字符串进行截取操作，返回一个新数组，新数组内容是截取的部分:一个参数且为正数时，将参数及其以后的全都截取；一个参数且为负数时，从尾部开始将参数及其之前的全部截取；两个参数时，第一个参数表示开始截取的下标，第二个参数表示结束截取的下标(不包括结束元素)

	var str="hello world";
	var newstr=str.slice(2);    
	console.log(newstr);//llo world
	
	var newstr=str.slice(2,3);
	console.log(newstr);//l  
substring( ):一个参数时，将参数及其以后的全都截取；两个参数时，第一个参数表示开始截取的下标，第二个参数表示结束截取的下标(不包括结束元素);

	var str="hello world";
	var newstr=str.substring(2);    
	console.log(newstr);//llo world
	
	var newstr=str.substring(2,3);
	console.log(newstr);//l  
substr( ):一个参数时，将参数及其以后的全都截取；两个参数时，第一个参数表示开始截取的下标，第二个参数表示截取的个数  
	
	var str="hello world";
	var newstr=str.substr(2);    
	console.log(newstr);//llo world
	
	var newstr=str.substr(2,5);
	console.log(newstr);//llo w  
###  2.复合数据类型  
Array数组、Object对象、Function函数  
###  Array数组([ ])  
###  声明方式:  
    var arr=new Array();
    arr[0]=1;arr[1]=2;
        
    var arr=new Array("hello","world");
        
    var arr=[1,2];  
###  方法:  
(1)length属性

	var arr=[1,2,3,4];
	console.log(arr.length);//4  
(2)push( )，用于向数组尾部添加元素

	var arr=[1,2,3,4];
	arr.push(5,6,"last");
	console.log(arr);//[1,2,3,4,5,6,"last"]  
(3)unshift( )，用于向数组前面追加元素

	var arr=[1,2,3,4];
	arr.unshift(0);
	console.log(arr);//[0,1,2,3,4]  
(4)pop( )，用于删除数组最后一个元素

	var arr=[1,2,3,4];
	arr.pop();
	console.log(arr);//[1,2,3]  
(5)shift( )，用于删除数组第一个元素

	var arr=[1,2,3,4];
	arr.shift();
	console.log(arr);//[2,3,4]  
(6)截取方式:  
splice( )，对数组元素进行增、删、改的操作，在原数组进行改动:一个参数时表示保留数组前n个元素；两个参数时第一个表示删除的起始位置，第二个参数表示删除的个数；三个及以上参数时第一个参数表示删除的起始位置，第二个参数表示删除的个数，第三个及以后的参数表示要替换的内容

	var arr=[1,2,3,4];
	arr.splice(2);
	console.log(arr);//[1,2]
	
	var arr=[1,2,3,4];
	arr.splice(1,2);
	console.log(arr);//[1,4]
	
	var arr=[1,2,3,4];
	arr.splice(1,2,6);
	console.log(arr);//[1,6,2]  
slice( )，对数组元素进行删除操作，返回一个新数组，新数组内容是删除的部分:一个参数且为正数时，删除该参数开始的元素到数组结束的所有元素；一个参数且为负数时，从数组尾部删除该参数开始的元素到数组开头的所有元素；两个参数时，第一个参数表示开始删除的下标，第二个参数表示结束删除的下标(不包括结束元素)
	
	var arr=[1,2,3,4];
	arr.slice(2);
	console.log(arr);//[3,4]
	
	var arr=[1,2,3,4];
	arr.slice(1,3);
	console.log(arr);//[2,3]  
(7)sort( )，对数组元素进行排序  
当变量a为字符串数组时，a.sort( )表示按每个元素的字符个数进行从小到大排序

	var arr=["wujiayi","helloword","smile"];
	arr.sort();
	console.log(arr);//["helloword", "smile", "wujiayi"]  
当变量a为数字数组时，a.sort( )表示按每个元素的首字母开始比较进行从小到大排序

	var arr=[1995,3,24];
	arr.sort();
	console.log(arr);//[1995, 24, 3]  
数字从小到大排序

    a.sort(function(a,b){return a-b})  
数字从大到小排序

    a.sort(function(a,b){return b-a})  
(8)reverse( ):数组为数字时，对数组进行从大到小排序；数组为字符串时，对数组元素进行反转

	var arr=[1,2,3];
	arr.reverse();
	console.log(arr);//[3,2,1]
	
	var arr=["hello","hehe","wu"];
	arr.reverse();
	console.log(arr);//["wu","hehe","hello"]  
###  Object对象({ })  
###  声明方式:  
    var obj=new Object{};
    obj={"name":"jiayi","age":23};
        
    var obj=new Object{"name":"jiayi","age":23};
        
    var obj={"name":"jiayi","age":23};  
###  时间对象:  
返回星期、月、日、时分秒、格林威治时间、时区

    var date=new Date( );
    
    var date=Date( );  
返回年份

    var date=Date( );
    var getYear( );  
以四位数字返回年份

    var date=Date( );
    var getFullYear( );  
返回月份(0~11，一月是0)

    var date=Date( );
    var getMonth( );  
返回一个月中的某一天(1~31)

    var date=Date( );
    var getDate( );  
返回一周中的某一天(0~6，周日是0)

    var date=Date( );
    var getDay( );  
返回小时(0~23)

	var date=Date( );
	var getHours( );  
返回分钟(0~59)

	var date=Date( );
	var getMinutes( );  
返回秒(0~59)

	var date=Date( );
	var getSeconds( );  
返回毫秒(0~59)

	var date=Date( );
	var getMilliseconds( );  
返回1979年1月1日至今的毫秒数
	
	var date=Date( );
	var getTime( );  
###  Function函数  
###  数字函数  
(1)Math.random( )随机函数  
(2)取整  
Math.floor( )向下取整  
Math.ceil( )向上取整  
Math.round( )四舍五入取整  
(3)Math.max( )求最大  
(4)Math.min( )求最小  
###  匿名函数  
自执行方法  
(1)函数外面用小括号包起来  
(2)函数前面加!  
(3)函数前面加+  
###  命名函数  
(1)有返回值的函数  
(2)有参数的函数  
确定参数个数  
不确定参数个数时，用arguments，只在函数内部起作用，并且永远指向当前函数的调用者传入的所有参数  
(3)又有返回值又有参数的函数  
###  函数声明提升问题:  
在创建函数的时候，在函数执行后面用声明的方式创建会报错，只有把它提升到前面才能执行，如:  

    foo();//函数声明
	foo_later();//报错foo_later is not a function
	function foo(){ 
		console.log('函数声明'); 
	}
	var foo_later = function(){ 
    	console.log('函数表达式'); 
    }
	
	var foo_later = function(){ 
    	console.log('函数表达式'); 
    }    
    foo();//函数声明
	foo_later();//函数表达式
	function foo(){ 
		console.log('函数声明'); 
	}  
###  3.类型转换  
###  数字和字符串  
数字->字符串用toString( )，返回一个新变量  
字符串->数字用parseInt( )，有返回值  
###  数组和字符串  
数组->字符串用join( )，里面的参数表示如何连接数组里面的每个元素，默认用逗号连接  
字符串->数组用split( )，里面的参数表示用什么来分割字符串  
##  四、语句  
###  1.弹出语句  
alert弹出框  
prompt输入框  
confirm确认框  
###  2.打印语句  
console.log( )  
###  3.分支(判断)语句  
if语句

    if(){
    
    }else{
    
    }
    
    if(){
       
    }else if(){
    
    }else{
    
    }  
switch语句

	switch(){
		case“ ”:      
			break; 
		default: 
			break;
	}  
###  4.循环语句  
for循环

	for(var i=0;i<4;i++){
		执行循环体;
	}  
while循环

	var i=0;                   
	while(i<3){
		执行循环体;
		i++；
	}  
do-while循环
	
	do{
		i++;
		执行循环体;
	}while(i<3)  
终止循环的方法  
(1)break，跳出循环，执行循环语句以后的代码  
(2)continue，跳出本次循环，去执行下一次循环