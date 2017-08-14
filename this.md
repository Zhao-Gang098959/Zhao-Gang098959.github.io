## this
>

### 函数里面的this始终指向window
>
	直接打印
	console.log(this) //window
>
	var a = 10;
	function a1(){
		console.log(this);//window
	}
	a1();
>
	this最终指向的是调用它的对象，这里的函数a实际是被Window对象所点出来的，下面的代码就可以证明
	function a(){
			console.log(this); //Window
	}	
	window.a();
>
	这里的this指向的是对象o，因为你调用这个fn是通过o.fn()执行的，那自然指向就是对象o，
	this的指向在函数创建的时候是决定不了的，在调用的时候才能决定，谁调用的就指向谁。
	var o = {
	user:"加菲猫",
		fn:function(){
			console.log(this.user);  //加菲猫
		}
	}
	o.fn();
>

### this始终指向函数的所有者

>
	var o = {
	    a:10,
	    b:{
	        a:12,
	        fn:function(){
	            console.log(this.a); //12
	        }
	    }
	}
	o.b.fn();
>
	情况1：如果一个函数中有this，但是它没有被上一级的对象所调用，那么this指向的就是window
	情况2：如果一个函数中有this，这个函数有被上一级的对象所调用，那么this指向的就是上一级的对象。
	情况3：如果一个函数中有this，这个函数中包含多个对象，尽管这个函数是被最外层的对象所调用，this指向的也只是它上一级的对象。
>
	var o = {
	    a:10,
	    b:{
	        //a:12,
	        fn:function(){
	            console.log(this.a); //12
	        }
	    }
	}
	o.b.fn();
	尽管对象b中没有属性a，这个this指向的也是对象b，因为this只会指向它的上一级对象，不管这个对象中有没有this要的东西
>

### 定时器里的this始终指向window
>
	setInterval(function(){
		console.log(this);//window
	},1000)
`我们定义的全局变量和全局的函数都被保存在了window对象下面`

### 构造函数版this：

>
	所谓构造函数，就是通过这个函数生成一个新对象（object）。这时，this就指这个新对象。
>
	function Fn(){
		this.user = "加菲猫";
	}
	var a = new Fn();
	console.log(a.user); //加菲猫
>
	为了表明这时this不是全局对象，我对代码做一些改变：
>
	var user = "欧迪";
	function Fn(){
		this.user = "加菲猫";
	}
	var a = new Fn();
	console.log(a.user); //加菲猫
### 通过call/apply调用
>
#### call()方法
	function Cat(name){ 
		this.name = name; 
		this.showName = function(){
    		alert(this.name);
		}
	}
	function Dog(name){ 
		this.name = name; 
	}
	var cat = new Cat("加菲猫");
	var dog = new Dog("欧迪"); 
	cat.showName.call(dog,"");
	原本执行结果应该弹出’加菲猫’，但是由于使用了call方法，相当于把cat下面的showName方法应用于dog,所以弹出的是‘欧迪'
#### apply()方法
>
	function fn1(a,b){  
		alert(this); 
		return a + b;
	}
	console.log(fn1.apply(document,[5,6]))  
	弹出的是document，打印的数值为11
	
#### 注意：
>
	1.这里call()和apply()都是用来改变this指向的，两者的功能完全一样，只是参数不同
	2.call第一个参数是this要指向的上下文，后面跟着的参数不固定，都是当成函数的参数传递进去
	3.apply第一个参数也是this要指向的上下文，后面是一个数组或者类数组，数组的每一项按照顺序当成是函数的参数传递进去