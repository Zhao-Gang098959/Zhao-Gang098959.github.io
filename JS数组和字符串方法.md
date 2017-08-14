# JS数组和字符串方法
## 数组方法
>
#### 1. 数组概念
	概念类似于其他语言, 是一种保存数据的有序列表.
	ECMAScript数组的每一项可以保存任意类型的数据.
	数组的大小可以动态调整, 可以随着数据的添加自动增长以容纳新增数据.
	
#### 2. 数组定义
>
##### 第一种: 使用Array构造函数.
	var arr1 = new Array();  //空数组
	var arr1 = new Array(20);//长度为20的数组
	var arr1 = new Array(1，2，3);//含有1，2，3的数组
	var arr1 =Array(1，2);//省略new创建
##### 第二种: 使用数组字面量表示法.
	var arr = [];//空数组
	var arr = [1，2，3];//含有1，2，3的数组
	
#### 3. 数组取值/赋值
>
	数组是有序数据列表. 取值和赋值都是通过下标得到.
	下标: 用来表示每个数据的位置信息, 从0开始计数.
	操作格式: 数组[下标]
	注: 数组中包含3个元素, 下标变化为0-2, 访问3时会超出数据范围
>
	var arr = [1，2，3];
	var a = arr[0];／／取值
	arr［1］= 10;/／赋值
	arr［3］ = arr[0];//错误写法
	
***
### Math数学对象
>
#### 1.Math.min()  求最小数
>
	console.log(Math.min([3,6,2,7,8]));//2
>
#### 2.Math.max()  求最大数
>
	console.log(Math.max(3,6,2,7,8));//8
`以上求最大数和最小数的放法只支持把需要比较的数字传递进来，不支持直接进行数组比较`
>
#### 3.Math.ceil() 上舍入 不管小数部分是多小，都会进行向上取整的操作
>
	console.log(Math.ceil(1.01));//2
	console.log(Math.ceil(1.9));//2
>
#### 4.Math.floor() 下舍入 不管小数部分是多大，都会进行向下取整的操作 
>
	console.log(Math.floor(1.99));//1
	console.log(Math.floor(1.01));//1
>
#### 5.Math.round() 四舍五入
>
	console.log(Math.round(1.4));//1
	console.log(Math.round(1.5));//2
#### 6.Math.random()取0-1中间的随机数 [0,1)  0 <= x < 1;
>
	for (var i = 0; i < 10; i++) {
	 	console.log(parseInt(Math.random()*10));
	}
>
#### 7.如果要取到[min,max)
>
	Math.random()*(max - min) + min;
	如果要取到（min,max] (5,9]
	Math.random()*(max-min) + min+1;
	Math.random()*(max - min + 1) + min
	如果要取到(min,max); 
	Math.random()*(max-min-1)+min+1
>
***
### 数组排序
#### 冒泡排序
`使用数组时, 很多时候需要将数组中的元素按照一定条件进行排序.  
冒泡排序是比较常见的排序算法.  
以为其原理跟水底气泡上升至水面很相似而得名  
冒泡排序涉及到双循环, 外层循环控制趟数, 内层循环控制比较次数`
>
	var arr = [3,2,4,5,1];
	for (var i = 0; i < 4; i++) {
		for (var j = 0; j < arr.length - i - 1; j++) {
			var temp = arr[j];
			if(arr[j] < arr[j + 1]){
				arr[j] = arr[j+1];
				arr[j+1] = temp;
			}
		}
	}
	console.log(arr);
	
***
### Array数组对象
#### 数组方法
>
##### 1.数组元素的插入删除
	push(元素): 从尾部添加新元素
	unshift(元素): 从头部添加新元素
	pop(): 从尾部弹出元素
	shift(): 从头部弹出元素
	splice(起始位置, 长度): 该方法从起始位置开始, 删除长度个元素
	splice(起始位置, 0, 要插入的元素1, 要插入的元素2, 要插入的元素3…): 从起始位置删除0个元素, 然后把要插入的元素从起始位置插入进数组
##### 2.数组元素的替换
	splice(要替换元素起始位置, 要替换元素的长度, 新替换的元素1, 新替换的元素2, , , ) 
##### 3.数组元素的排序
>
	sort(): 方法能实现数组的排序(按照ASICC表的顺序排序)
>
	var arr = [1,3,8,2,5];
	console.log(arr.sort());// [1, 2, 3, 5, 8]
	console.log(arr);// [1, 2, 3, 5, 8]
	将数组排序 会改变原数组
>
	sort()方法如果想按照从大到小或者从小到大的方式排序，需要我们传递参数，参数的形式是函数
	升序 
	function asce(a,b){
		return a-b;
	}
	降序
	function desc(a,b){
		return b-a;
	}
	
##### 4.数组的拼接
>
	concat(): 方法可以实现两个数组的拼接
>
	var arr3 = [1,2,3];
	console.log(arr3.concat(4,5));//[1,2,3,4,5]
>
	concat()方法参数可以是数字，也可以是数组，
	如果是一维数组的话，会把合并数组拉伸，跟原数组合并为同一个数组；
	但是如果是二维数组或者多维数组的话，只会将合并数组的第一层拉伸合并，保留内层的数组
##### 5.数组元素之间添加分隔符
>
	join(): 方法可以使用括号中的参数作为数组中的元素分隔符
>
	var arr = [1,2,3,4];
	console.log(arr.join().length);//"1,2,3,4"
##### 6.reverse()  将字符串逆序 会修改原数组
	var arr1 = ["nihao","shijie","biancheng"];
	console.log(arr1.reverse());
	console.log(arr1);
##### 7.slice()  返回数组的某一部分 不会改变原数组
>
	var arr = ["123","456","789","1","2","3"];
	两个参数，第一个表示开始截取的位置，第二个表示截取到的位置，前闭后开
	console.log(arr.slice(2,5));
	当只有一个参数时，这个参数表示开始截取的下标位置，一直截取到数组的最后一项
	console.log(arr.slice(1));／／["456", "789", "1", "2", "3"]
	console.log(arr);／／["123", "456", "789", "1", "2", "3"]
##### 8.splice()  数组拼接 会修改原数组
>
	var arr = ["this","is","a","very","boring","thing"];
	有三个参数，1表示插入的下标位置  2表示删除多少项  3表示插入的内容	arr.splice(4,1,"interesting");
	console.log(arr);／／["this", "is", "a", "very", "interesting", "thing"]
##### 9.pop()移除数组中的最后一个元素并返回该元素
>
	var arr = [1,2,3,4,5];
	console.log(arr.pop());
	console.log(arr);／／[1, 2, 3, 4]
##### 10.shift()移除数组中的第一个元素并返回该元素
>
	var arr = [1,2,3,4,5];
	console.log(arr.shift());
	console.log(arr);／／[2, 3, 4]
##### 11.push() 往数组的最后添加一项内容，返回的是新数组的长度，会修改原数组
	var arr = ["this","is","a","beauty"];
	console.log(arr.push("girl"));
	console.log(arr);//["this", "is", "a", "beauty", "girl"]
>
##### 12.unshift() 往数组的第一项添加内容，会修改原数组 返回的是新数组的长度
	var arr = [1,2,3,4];
	console.log(arr.unshift(0));
	console.log(arr);//[0, 1, 2, 3, 4]
>
##### 13.indexOf() 检测数组是否包含某一项内容，如果是，返回下标，如果没有，返回-1
	 var arr = ["张三","李四","王五","任六"];
	 console.log(arr.indexOf("任六"));／／6
>
##### 14.lastIndexOf() 跟indexOf()类似 从后往前查找
>
#### 新增数组方法
##### 1.forEach() 遍历数组 参数是匿名函数，匿名函数接受1-3个形参
	第一个形参表示数组的每一项内容
	第二个形参表示每一项内容所对应的下标
	第三个形参表示原数组 
>
	var arr = ["haha","hehe","heihei","xixi","hoho"];
	arr.forEach(function(x,y,z){
		console.log(x,y,z);//haha 0 
	})
##### 2.map() 映射 参数接受一个匿名函数，匿名函数可以传递两个形参
>
	第一个 原数组里的每一项内容
	第二个 原数组里每一项内容对应的下标
	var arr1 = [1,3,5,7,9];
	arr1.map(function(x,y){
		console.log(x,y);//1 0
	})
##### 3.filter() 过滤
>
	var arr3 = [100,300,500,700,600,50,20];
	function price(num){
		return num < 300;
	}
	console.log(arr3.filter(price));//[100, 50, 20]
##### 4.every() 判断么每一个是否满足条件，返回true或false
>
	var arr4 = [1,2,3,8,9];
	console.log(arr4.every(function(x){
		return x < 10;／／true
	}))
##### 5.some() 判断么每一个是否满足条件,只要有满足条件的就反悔true，否则返回false
>
	var arr5 = [1,2,3,5,10,20];
	console.log(arr5.some(function(y){
		return y < 5;//true
	})) 
#### 二维数组
>
	二维数组
	数组的维度和空间的维度不一样, 二维数组就是, 数组中的每个元素都是一个数组.
>
	var arr = [
			[[100,50],[200,100]],
			[300,150]
			];
	console.log(arr[0]);//[100,50],[200,100]
	console.log(arr[0][1][1]);//100
	
***
##字符串方法
##### 1.indexOf() 查找字符串出现的位置 返回该字符串的下标,如果查询的字符在对应的字符串里找不到，则返回-1
>
	参数可以传两个：
	第一个参数：要查找的字符串
	第二个参数（可选）：开始查找的下标位置
>
	var str = "hello world";
	字符串也是有长度的，用length来访问
	注意：字符串里的空格也占位置
	console.log(str.length);//11
	console.log(str.indexOf("l"));//2
	console.log(str.indexOf("y"));//-1
##### 2.lastIndexOf()跟indexOf()类似，在一个字符串中的指定位置从后向前搜索。
>
	console.log(str.lastIndexOf("wo"));//6
	//整体查找的话，无论是从前往后找，还是从后往前找，返回的都是第一个字母出现的下标
##### 3.slice()截取字符串的某一部分
>
	有两个参数：1.表示开始截取的下标位置
				2.表示截取到的下标位置
	该方法不会改变原来的字符串
	[0,1)
	所有的截取字符串的操作，截取的范围都是前闭后开。
	第二个参数 - 第一个参数 = 截取字符串长度
	var str = "hello world";
	console.log(str.slice(0,5));
	console.log(str.slice(2));//hello world
	如果只传递一个参数，那这个参数会视为开始截取的下标，默认截取到字符串的最后一位
	console.log(str.slice(9,1));
	如果没有参数，那默认截取整个字符串
##### 4.substring() 截取字符串
	有两个参数：1.表示开始截取的下标位置
			2.表示截取到的下标位置
	不会改变原字符串
	如果只传递一个参数，那这个参数会视为开始截取的下标，默认截取到字符串的最后一位
	如果没有参数，那默认截取整个字符串
>
	var str = "hello world";
	console.log(str.substring(0,5));//hello
	console.log(str.substring(9,1));/ello wor
	subtring()方法会自动比较两个参数的大小，如果我们给的第一个参数大于第二个的话，那该方法会自动进行参数位置的调整
##### 5.split()把字符串分割成字符串数组
>
	如果没有参数，那原字符串就是转化数组的唯一一项内容
>
	var str = "12345674891042354678";
	console.log(str.split("4"));//["123", "567", "8910", "235", "678"]
	// 如果有一个参数，那这个参数就是字符串分割的依据
	console.log(str.split("4",2));//["123", "567"]
	//如果有第二个参数，那第二个参数表示数组的长度
##### 6.charAt() 返回下标位置所对应的字符
>
	var str = "abcdef";
	var str1 = "1234";
	console.log(str.charAt(2));//c
	参数：1个，表示要获取字符的下标
	console.log(str.charAt());//a
	如果不写参数，默认返回字符串第一位上的字符
##### 7.charCodeAt() 返回下标位置对应字符的Unicode编码
>
	console.log(str1.charCodeAt(0));//49
	console.log(str1.charCodeAt(1));//50
##### 8.replace()  字符串替换
>
	两个参数：1.被替换的字符串
			2.替换的字符串
	不会改变原字符串
>
	var str = "高考分数查询：你考了300分";
	console.log(str.replace("300","700"));//高考分数查询：你考了700分
	console.log(str);//高考分数查询：你考了300分
##### 9.toLowerCase()  把字符串转换为小写
>
	var str = "Hello World";
	console.log(str.toLowerCase());//hello world
##### 10.toUpperCase()  把字符串转换为大写
>
	console.log(str.toUpperCase());//HELLO WORLD
##### 11.trim()去掉字符串前后的空格
	var str = " hello world ";
	console.log(str.length);//13
	console.log(str.trim().length);//11