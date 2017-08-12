# this指向  
## 指向window  
	function test(){
		var a="jiayi";
		console.log(this.user);//undefined
		console.log(this);//Window
	}
	test();  
### 实际上this的最终指向是调用它的对象，而这里的函数test是被window对象调用出来的，因此指向window。  
而上面的函数实际上是下面这种形式：  
	
	function test(){
		var a="jiayi";
		console.log(this.user);//undefined
		console.log(this);//Window
	}
	window.test();  
***  
## 指向对象  
	var test={
		a="jiayi";
		b:function (){
			console.log(this.a);//jiayi
		}
	}
	test.b();  
### window是JS中的全局对象，我们创建的变量都是在给window添加属性，所以这里是给window添加了一个test对象属性，而函数b的上一级是test对象，结果也是由test对象调用，就像上面说的，this的最终指向是调用它的对象，所以这个函数的指向就是test，而test的a属性值就能打印出来。  
同样上面的函数实际上是下面的形式：  
	
	var test={
		a="jiayi";
		b:function (){
			console.log(this.a);//jiayi
		}
	}
	window.test.b();  
***  
### 当函数中包含多个对象的时候，尽管函数是被最外层调用，this指向也永远是它的上一级，如下：  

	var test={
		a=10;
		b:{
			a=12;
			c:function(){
				console.log(this.a);//12
			}
		}
	}
	test.b.c();  
### this指向b，所以调用到b里面的a的值，因此打印出来的值为12。  
***  
### 还有一种情况是函数被上一级引用而指向window，如  

	var test={
		a=10;
		b:{
			a=12;
			c:function(){
				console.log(this.a);//undefined
				console.log(this);//Window
			}
		}
	}
	var fn=test.b.c; 
	fn();  
### 虽然函数被b引用，但在赋值给fn的时候，b并没有被调用，因此就像一开始指向window时提过的，fn()变成赋给window的变量，所以this指向变为window，自然也就调用不到b里面a的值，因此this.a打印出来的结果为undefined。  
***  
## 构造函数指向  
	function Fn(){
		this.name="jiayi";
	}
	var a=new Fn();
	console.log(a.name);//jiayi  
### new关键字可以改变this的指向，所以声明的对象a调用函数Fn，this的指向就为a。  
***  
## call和apply改变this指向  
### call和apply是构造函数中继承的一种形式，继承的原理就是改变this的指向，如：  
	function Cat(name){
		this.name=name;
		this.show=function(){
			console.log(this.name);//小狗
		}
	}
	function Dog(name){
		this.name=name;
	}
	var cat=new Cat("小猫");
	var dog=new Dog("小狗");
	cat.show.call(dog,"");
	cat.show.apply(dog,[""]);  
### 原本this指向cat，但是，因为用了call和apply的继承方法，第一个参数表示改变this的指向为dog，，因此打印出来的结果就是小狗而不是小猫。