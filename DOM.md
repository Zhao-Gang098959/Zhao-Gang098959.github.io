
## Document Object Model   文档对象模型  
`DOM 是 W3C（万维网联盟）的标准
W3C 文档对象模型 （DOM） 是中立于平台和语言的接口，它允许程序和脚本动态地访问和更新文档的内容、结构和样式。
DOM 是关于如何获取、修改、添加或删除 HTML 元素的标准。
`
***

### 什么是DOM
Document Object Model   文档对象模型    
DOM 是 W3C（万维网联盟）的标准  
W3C 文档对象模型 （DOM） 是中立于平台和语言的接口，它允许程序和脚本动态地访问和更新文档的内容、结构和样式。  
DOM 是关于如何获取、修改、添加或删除 HTML 元素的标准。

#### 1.dom按照层级的形式来划分
	父（parent）、子（child）和同胞（sibling）等术语用于描述这些关系。父节点拥有子节点。同级的子节点被称为同胞（兄弟或姐妹）。
		在节点树中，顶端节点被称为根（root）
		每个节点都有父节点、除了根（它没有父节点）
		一个节点可拥有任意数量的子
		同胞是拥有相同父节点的节点
![haha](http://www.w3school.com.cn/i/dom_navigate.gif)
>

#### 实例
>
	<html>
	  <head>
	    <title>DOM 教程</title>
	  </head>
	  <body>
	    <h1>DOM 第一课</h1>
	    <p>Hello world!</p>
	  </body>
	</html>
>
	从上面的 HTML 中：
	<html> 节点没有父节点；它是根节点
	<head> 和 <body> 的父节点是 <html> 节点
	文本节点 "Hello world!" 的父节点是 <p> 节点
	并且：
	<html> 节点拥有两个子节点：<head> 和 <body>
	<head> 节点拥有一个子节点：<title> 节点
	<title> 节点也拥有一个子节点：文本节点 "DOM 教程"
	<h1> 和 <p> 节点是同胞节点，同时也是 <body> 的子节点
	并且：
	<head> 元素是 <html> 元素的首个子节点
	<body> 元素是 <html> 元素的最后一个子节点
	<h1> 元素是 <body> 元素的首个子节点
	<p> 元素是 <body> 元素的最后一个子节点
	
#### 2.按照节点类型划分

>
	1元素节点
	2属性节点
	3文本节点
	9document节点
	8注释节点
>
	nodeType 属性返回以数字值返回指定节点的节点类型。
	如果节点是元素节点，则 nodeType 属性将返回 1。
	如果节点是属性节点，则 nodeType 属性将返回 2。
	console.log(document.nodeType);//9
>
	nodeName 属性指定节点的节点名称。
	如果节点是元素节点，则 nodeName 属性返回标签名。
	入股节点是属性节点，则 nodeName 属性返回属性的名称。
	对于其他节点类型，nodeName 属性返回不同节点类型的不同名称。
>
	var div = document.getElementsByTagName('div')[0];
	console.log(div.nodeName);//DIV
>
	nodeValue 属性设置或返回指定节点的节点值。
	注释：如果您希望返回元素的文本，请记住文本始终位于文本节点中，并且您必须返回文本节点的值（element.childNodes[0].nodeValue）。
	提示：nodeValue 属性的替代选择是 textContent 属性。
	
***

### HTML DOM 对象 - 方法和属性
#### 获取子节点
>
	children/childNodes 获取指定元素的第一层子节点
	区别：children 在标准浏览器和IE9下，不会造成空白文本解析，获取到的是真实的子节点，不支持IE6/7/8  
	childNodes 会解析空白文本节点
>
	firstChild/firstElementChild
	获取指定元素的第一个子节点
	区别：
	firstChild 在标准和ie9下会获取到空白文本节点。
	firstElementChild  标准下获取最后一个子元素节点，ie6/7/8不支持。 	childNodes 获取元素所有的子节点，包括空白文本节点 	hasChildNodes()  判断指定元素是否拥有子节点，返回布尔值true或false
>
	lastChild/lastElementChild
	获取指定元素的最后一个子节点
	区别：
	lastChild 在标准和ie9下会获取到空白文本节点。
	lastElementChild  标准下获取最后一个子元素节点，ie6/7/8不支持。
>
	previousSibling/previousElementSibling 获取指定元素的上一个兄弟节点
	nextSibling/nextElementSibling
	获取指定元素的下一个兄弟节点点
	区别：
	previousSibling 在标准和ie9下会获取到空白文本节点。
	previousElementSibling  标准下获取最后一个子元素节点，ie6/7/8不支持
>
	parentNode 获取指定元素的父节点
	offsetParent  获取离指定元素最近的具有定位属性的祖先节点
	以上两个属性都是把获取到的元素结构整体返回，不仅仅只是返回一个标签
>
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
	</head>
	<body>
		<ul id="list">
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
		</ul>
	</body>
	<script>
		var list = document.getElementById('list');
		console.log(list.children)
		console.log(list.childNodes);
		console.log(list.firstChild);//text
		console.log(list.firstElementChild);//<li>1</li>
		console.log(list.lastChild);//text
		console.log(list.lastElementChild);//<li>5</li>
		console.log(list.firstElementChild.nextSibling);
		console.log(list.firstElementChild.nextElementSibling);
		console.log(list.lastElementChild.previousElementSibling);
		console.log(list.lastChild.nodeValue);
		console.log(list.firstElementChild.firstChild.nodeValue);
	</script>
	</html>
	
***
### 获取与元素属性的方式
>
	1.元素.属性名  获取不到非标准属性
		注意：如果获取的是元素的class的话，在写的时候必须是className
		console.log(box.className)
>
	2.["属性名"]  同上
	console.log(box["className"])
>
	3.getAttribute("属性名")  获取元素属性
		可以获取到元素的自定义属性
		box.getAttribute("ceshi")
		attributes能访问到元素上所有的属性,返回的是一个类数组，我们可以通过下标的形式拿到每一个属性
		console.log(box.attributes[0]);
		var arr = box.attributes;
***

## 增删改查
>
	创建节点  document.createElement('标签名')
	var div = document.createElement('div');
>
	appendChild() 给指定元素追加子节点
	document.getElementsByTagName('body')[0].appendChild(div);
>
	插入元素  insertBefore(插入的元素,参照元素)
	body.insertBefore(div,body.lastElementChild.previousElementSibling);
>
	removeChild()  移除子节点
	body.removeChild(body.lastElementChild.previousElementSibling);
>
	cloneNode() 克隆节点 接受一个布尔值作为参数  
	当参数为true时，会克隆元素的innerHTML，false不会，默认是false
>
	hasChildNodes()  判断指定元素是否拥有子节点，返回布尔值true或false
	console.log(body.hasChildNodes());
>
	childNodes 获取元素所有的子节点，包括空白文本节点
	console.log(body.childNodes[3]);
	
***
## innerHTML 属性
获取元素内容的最简单方法是使用 innerHTML 属性。  
innerHTML 属性对于获取或替换 HTML 元素的内容很有用。
>
	<body>
		<p id="intro">Hello World!</p>
	<body>
	<script>
		var txt=document.getElementById("intro").innerHTML;
		document.getElementById("p").style.color="blue";//改变样式
		document.write(txt);
	</script>
	
***
## 事件
>
	点击事件
	open.onclick = function(){
		box.style.display = "block";
	}
>
	onmousedown、onmouseup 以及 onclick 事件
	onmousedown、onmouseup 以及 onclick 事件是鼠标点击的全部过程。首先当某个鼠标按钮被点击时，触发 onmousedown 事件，然后，当鼠标按钮被松开时，会触发 onmouseup 事件，最后，当鼠标点击完成时，触发 onclick 事件。  
	box.onmousedown = function(){
		this.style.background = "red";
	}
	box.onmouseup = function(){
		this.style.background = "green";
	}
>
	onmouseover 当鼠标移入时触发的事件
	box.onmouseover = function(){
		this.style.background = "pink";
	}
>
	//onmouseout 当鼠标移出时触发的事件
	box.onmouseout = function(){
		this.style.background = "red";
	}
	

***
### HTML DOM 节点列表长度
length 属性定义节点列表中节点的数量。
>  
您可以使用 length 属性来循环节点列表：
>
	for (i=0;i<x.length;i++)
>
	{
		