## js数据类型
***
### 1.typeof 获取数据类型
>
	数字类型在js里不分整形和浮点型; 
	var num1 = 10;    
	var num2 = 10.1;  
		console.log(typeof num2);     
>
	单引号或者双引号包裹的内容都属于字符串  
	var str = "你好";
	console.log(typeof str); 
>
	boolean布尔类型 有两个布尔值 true false
	var bool = 'false';
	console.log(typeof bool);
	

### 2.number 数字类型
>
	显示类型转换 
	Number()  转换为数字
	console.log(typeof Number(str)); //NaN
>
	NaN not a number 不是一个数字 数字类型的一种  与任何值都不想等，包括他自己  
	parseInt()  parseFloat() 强制转换为数字类型  
	从左到右进行数字的提取，遇到非数字返回
	如果最开始就提取不到数字，返回NaN


### 3.string 字符串类型
>
	String() 转换为字符串类型
	console.log(typeof String(undefined));


### 4.undefined 未定义类型
>
	var d;  //无初始值undefined
	

### 5.null 空类型
>
	var e = null;	//空对象类型
	
***
## js数据类型转换
### 1.显示类型转换 
>
	Number()  转换为数字
	console.log(typeof Number(str)); //NaN
	NaN not a number 不是一个数字 数字类型的一种  与任何值都不想等，包括他自己
	console.log(NaN == NaN);//false
	console.log(Number(true));//1
	console.log(Number(false));//0
	console.log(Number(undefined));//NaN
	console.log(Number(null));//0
>
	String() 转换为字符串类型
	console.log(typeof String(undefined));
>
	Boolean()  非零即为真
	console.log(Boolean(11));
	console.log(Boolean(0));
	console.log(Boolean(-1));
	console.log(Boolean(null));//false
	console.log(Boolean(NaN));//false
>
	parseInt()  parseFloat() 强制转换为数字类型  
	从左到右进行数字的提取，遇到非数字返回
	如果最开始就提取不到数字，返回NaN
>
	parseInt()  取整
	console.log(parseInt(true));//NaN
	console.log(parseInt(12.5678));//12
	console.log(parseInt("ab123cd"));//NaN
>
	parseFloat() 取小数
	console.log(parseFloat("12.5678"));
	
### 2.隐式类型转换
>
	var a = 10;
	var b = "10";
	console.log(typeof(a + "")); //string
	console.log(typeof + b);  //number
	隐式类型转换
	数字 ＋ 字符串  得到字符串
	+ 字符串  得到数字类型  ＋号相当于取正数
***


## js变量
>
### 直接量(literal): 
		程序中直接使用的数据值.
### 变量(variable):
		变量是使用var关键字(关键字: ECMA-262描述了一组具有特定用途的关键字, 用于系统执行特定操作, 也成保留字)定义的一个存储空间, 用来保存数据.
		js的变量是松散类型(弱类型), 可以用来保存任何类型的数据
### 命名规范
	在程序中, 凡是出现名字的地方(变量名/属性名/函数名/方法名), 都可以遵循如下命名规范: 
	1.由数字/字母/下滑线(_)/美元符($)构成, 第一个字符不能为数字
	2.驼峰命名法
	3.避免和系统关键字重复
	4.区分大小写
	
***
## 操作符
>
	+  加法运算和字符串拼接
	console.log(1+2);
	console.log(1 + null);//1
	console.log(1 + undefined);//NaN
	console.log(1 + true);//2
	+前后都是数字类型的话，进行加法运算，
	如果+前后由任何一边是字符串类型，+号的作用就是进行字符串拼接
>
	- 减法运算
	console.log(3 - 1);//2
	console.log(5 - true);//4
	console.log(3 - "123abc123");//NaN
	console.log(3 - "123");//-120
	//数字和非数进行减法运算，结果还是非数
	console.log(3 - undefined);//NaN
	console.log(3 - null);//3
	>
	 * 乘法运算
	console.log(3 * 5);//1
>
	 / 除法运算
	console.log(10 / 2); //5
>
	 % 取余数，求模
	console.log( 9 % 4);//1
>
	复合运算符  +=  -=
	var a = 2;
	var b = 1;
	a += b;  //  a = a + b
	a -= b;  //  a = a - b
	
	//赋值运算符
	// = 表示赋值  把等号右边的值赋给等号左边

	// == 表示比较
	
***
## 分支语句1
>
	if…
	如果...就...  
	if (条件) {
    // 语句
	}  
	if(false){
		console.log("条件成立，执行");
	}
>
	if…else…
	如果…就...否则…
	if (条件) {
    // 语句1
	} else {
    // 语句2
>
	if…else if…
	如果…就...
	否则如果…就…
	if (条件1) {
    // 语句1
	} else if (条件2) {
    // 语句2
	} else {
    // 语句3
	}
	
***
## 多分支
>
	switch (条件) {  
		case 情况1:  
			语句;
        break;
        case 情况2:
      	  	语句;
       	 break;
       	 case 情况2:
      	 	 语句;
      	  break;
    	default: 
        	语句;
	}
>
`注意事项:
	1.switch语句中的break表示结束当前的情况, 如果当前case中没有break, 会跳入下一个case继续执行, 直到找到break退出  
	2.根据对应条件可以执行case, 条件以外的判断会进入default执行  
	3.在js中, switch和case的值可以是常量/变量/表达式`
	
***

## 循环
	循环语句, 满足条件下重复执行语句的结构.  
	主要变现形式有三种, for循环, while循环, do…while循环.  
	三种循环结构不同, 原理相同, 适应于不同的情况.
### for循
>
	for (循环变量初始化; 循环条件; 循环变量变化) {
    循环语句;
	}	
	var num = 0;	
	for (var i = 0; i <= 10; i++) {  
			num += i;
			console.log(num);
	}
	1+2+3+4+5+6+7+8+9+10	
		
### while循环
>
	while (循环条件) {
		循环语句;
		循环变量变化;
	}
	var i = 1;
	while(i < 10){
		if( i % 2 == 0){
			console.log(i);
		}
		i += 1;
	}
	2,4,6,8
	
### do...while...
>
	do {
    	循环语句;
    	循环变量变化;
	} while (循环条件)
	var i = 1;
	do{
		console.log(i);
		i++;
	}while(i < 5);
	console.log(i);
`do...while循环跟while循环的区别：  
while循环是只有满足循环条件的前提下，才会执行循环语句。不满足，不执行。
do..while循环，会先执行一遍do里面的内容，然后再判断循环条件是否满足，如果满足继续执行，如果不满足则终止`

## 循环注意事项
>
循环本质没有区别, 不同形式之间可以相互转化.  
不同形式的循环是为了适应不同的操作情景.  
已知次数的循环一般使用for循环.  
未知次数的循环一般使用while循环.   
do…while循环使用较少.

***

## 循环控制
### break语句控制
>
break语句会立即退出本层循环, 循环终止.
>
	for(var i=0;i<5;i++){
		if(i==3){
			break;//循环打断
		}
		console.log(i);//打印结果：0，1，2
	}
	
### continue语句控制
continue语句会立即跳过本次循环, 循环继续.
>
	for(var i=0;i<5;i++){
		if(i==3){
			continue;//循环打断
		}
		console.log(i);//打印结果：0，1，2,4,5
	}
	
***

### 循环嵌套
循环中的循环语句也可以是一个循环.  
循环嵌套一般用于行列内容操作/排序操作等.
>
	第一层for循环控制的是循环多少次
	for (var i = 0; i < 10; i++) {
		// 第二层for循环控制的是每次走多少遍
		for (var j = 0; j <= i; j++) {
			document.write("*");
		}
		document.write("<br>");
	}
	打印结果
	*
	**
	***
	****
	*****
	******
	*******
	********
	*********
	**********
	
***
### 函数
1.命名函数  function fnName(){}  
2.匿名函数


>
### 函数的基本要素
	1.要用function关键字定义
	2.函数要用对应的函数名 当然匿名函数除外
	3.函数调用方式  函数名()
	注意：函数不调用不执行
	4.函数返回值要用return关键字
		返回的内容放到return之后
		注意：return之后的任何代码都将不会执行
### 函数名()
>
	会使函数立即执行，当我们希望在某个事件触发之后执行函数的话，那只需要在给事件赋值函数的时候把函数名写上就可以了，一定不要加括号

`函数里面的this默认指向window,但是当我们的函数有所属关系的时候，函数里的this指向函数的所有者`
### 函数的返回值
>
#### 1.无参数无返回值
	function fn1(){
		console.log("我是一个无参数无返回值的函数");
	}
	fn1();
#### 2.无参数有返回值
	function fn2(){
		console.log("我是一个函数");
		return true;//函数的返回值
	}
	console.log(fn2())
#### 3.有参数无返回值
				//形参
	function fn3(name,age,sex){
		console.log("我是"+name+"，我今年"+age+"岁"+"我是"+sex+"生");
	}
		//实参
	fn3("张三","20","男");
	fn3("李四","22","女");
#### 4.有参数有返回值
	function fn4(a,b){
		// console.log(a + b);
		return a + b;
	}
	console.log(fn4(12,5))
`JS中的函数默认会返回undefined，如果我们给函数定义了返回值，以我们设置的返回值为准`

## 全局变量、局部变量

### 1.局部变量 
 
>
	在函数内部，用var关键字定义的变量叫局部变量
	var num = 10;//全局变量
		function fn1(){
		console.log(num);
	}
	fn1();

### 2.全局变量
	在函数外部定义的变量以及一些在函数内部没有var关键字的变量 都是全局变量  
	局部变量的优先级要高于全局变量

	区别：全局变量在整个js代码中都可访问；
	局部变量只能在函数内部访问
	简单来讲：在函数内部可以访问到全局变量，但是在函数外部访问不到局部变量
	
	js垃圾回收机制：
	全局变量是当整个页面关闭或者js代码执行完毕才会销毁局部变量 是当函数执行完毕，局部变量就会被销毁
	
	function fn2(){
		var str = "hello";//局部变量
		console.log(str);
		// return str;
		//函数的返回值跟局部变量是两种完全不同的概念，不要混淆
	}
	//console.log(str);
	var str = fn2();
	console.log(str);
	
## 变量声明提升
浏览器在读取我们代码的时候会先把变量名和函数名抓取到，然后在当前作用域的最顶层进行声明
>
	fn1();
	function fn1(){
		alert(1);
	}
	//fn1();
	function fn2(){
		var str;//浏览器帮我们进行的操作，变量声明提升到当前作用域的最顶层
		//console.log(str);
		//var str = "nihao";
		str = "nihao";
	}
	fn2();
	var num = 10;//全局变量
	function fn3(){
		var num;
		console.log(num);//undefined
		num = 5;
		console.log(num);//5
	}
	fn3();
	console.log(num);//10
	function fn4(){
		var num = 3;//局部变量
		console.log(num);
	}
	fn4();
	var num1 = 1;
	function fn5(){
		// console.log(num1);
		num1 = 10;//对全局变量的重新赋值
	}
	fn5();
	console.log(num1)
	var num2 = 10;
	num2 = 5;


	

