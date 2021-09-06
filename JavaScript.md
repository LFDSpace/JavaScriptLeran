# JavaScript

- 运行在浏览器的脚本语言（目标程序以文本格式打开）
- 用于网页和用户之间的交互，比如提交的时候，进行用户名是否为空的判断
- Java运行在JVM当中，JavaScript运行在浏览器的内存当中
- 完整的javascript由语言基础,BOM,DOM组成

###### JavaScript包括三大块：

**ECMAScript**：JS的核心语法（ES规范 / ECMA-262标准）
**DOM**：Document Object Model（文档对象模型：对网页当中的节点进行增删改的过程。）HTML文档被当做一棵DOM树来看待。

```javascript
var domObj = document.getElementById("id");
```

**BOM**：Browser Object Model（浏览器对象模型）
关闭浏览器窗口、打开一个新的浏览器窗口、后退、前进、浏览器地址栏上的地址等，都是BOM编程

## 1.入门案例

script标签javascript代码必须放在script标签中
**用户点击以下按钮，弹出消息框**
html中嵌入javascript有**三种方式**

### 第一种方式

- 事件句柄=“js代码”，把这段代码注册到onclick之后，有操作后，js代码会在浏览器被自动调用
- 弹窗消息的用法是：window.alert(“消息”)
- JS中的一条语句结束之后可以使用分号“;”，也可以不用
- JS中的字符串可以使用双引号，也可以使用单引号

###### 具体alert的用法内双外单或者内单外双

```javascript
<input type="button" value="hello" onclick="window.alert('hello js')"/>
<input type="button" value="hello" onclick='window.alert("hello jscode")'/>

```

###### alert弹窗中window可以省略

```javascript
<input type="button" value="hello" onclick='alert("hello jscode")'/>
```

##### 完整示例代码

```html
<!doctype html>
<html>
	<head>
		<title>HTML中嵌入JS代码的第一种方式</title>
	</head>
	<body>
		
		<!--
			1、JS是一门事件驱动型的编程语言，依靠事件去驱动，然后执行对应的程序。
			在JS中有很多事件，其中有一个事件叫做：鼠标单击，单词：click。并且任何
			事件都会对应一个事件句柄叫做：onclick。【注意：事件和事件句柄的区别是：
			事件句柄是在事件单词前添加一个on。】，而事件句柄是以HTML标签的属性存在
			的。

			2、οnclick="js代码"，执行原理是什么？
				页面打开的时候，js代码并不会执行，只是把这段JS代码注册到按钮的click事件上了。
				等这个按钮发生click事件之后，注册在onclick后面的js代码会被浏览器自动调用。
			
			3、怎么使用JS代码弹出消息框？
				在JS中有一个内置的对象叫做window，全部小写，可以直接拿来使用，window代表的是浏览器对象。
				window对象有一个函数叫做:alert，用法是：window.alert("消息");这样就可以弹窗了。
			

		-->
		<input type="button" value="hello" onclick="window.alert('hello js')"/>

		<input type="button" value="hello" onclick='window.alert("hello jscode")'/>

		<input type="button" value="hello" onclick="window.alert('hello zhangsan')
													window.alert('hello lis')
													window.alert('hello wangwu')"/>
		
		<!-- window. 可以省略。-->
		<input type="button" value="hello" onclick="alert('hello zhangsan')
													alert('hello lis')
													alert('hello wangwu')"/>

	</body>
</html>

```

### 第二种方式

通过脚本块的方式，页面打开的时候执行，并且遵守自上而下的顺序依次逐行执行。（这个代码的执行不需要事件）。（CSS为样式块）

- javascript的脚本块在一个页面当中可以出现多次。没有要求
- javascript的脚本块出现位置也没有要求，随意
- alert有阻塞当前页面加载的作用。（阻挡，直到用户点击确定按钮。）

###### 脚本块的格式为script

```html
<script type="text/javascript">
window.alert("first.......");
</script>
```

##### 完整代码如下

```html

<script type="text/javascript">
window.alert("first.......");
</script>

<!doctype html>
<html>
	<head>
		<title>HTML中嵌入JS代码的第二种方式</title>
		<script type="text/javascript">
			window.alert("head............");
		</script>
	</head>
	<body>

		<input type="button" value="我是一个按钮对象1" />
		
		<!--第二种方式：脚本块的方式-->
		<script type="text/javascript">

			window.alert("Hello World!"); // alert函数会阻塞整个HTML页面的加载。
		</script>

		<input type="button" value="我是一个按钮对象" />

	</body>
</html>

```

### 第三种方式

外部引入js文件

- 同一个js文件可以被引入多次，但实际开发中这种需求很少
- 引入js文件的同时再写代码，文件会被执行，但代码块不会被执行。但分别两个script，一个引入一个写代码是可以的

```html
<!doctype html>
<html>
	<head>
		<title>HTML中嵌入JS代码的第三种方式：引入外部独立的js文件。</title>
	</head>
	<body>
		
		<script type="text/javascript" src="js/1.js">
			// 这里写的代码不会执行。
			// window.alert("Test");
		</script>

		<script type="text/javascript">
			alert("hello jack!");
		</script>


	</body>
</html>

```

js文件

```javaScript
window.alert("hello js!");
window.alert("hello js!");
window.alert("hello js!");

```

# 2.变量

## 2.1变量的声明与赋值

- java中要求变量声明的时候是什么类型，不可变。编译期强行固定变量的数据类型称为强类型语言。`数据类型 变量名;`
- 对比javascript，javascript是一种弱类型语言，没有编译阶段，一个变量可以随意赋值，赋什么类型的值都行，`var 变量名;`

在js中可以执行，但在java中不能执行

```javascript
var i = 100;
i = false;
i = "abc";

```

- 当系统没有赋值的时候，会默认给undefined，undefined是系统的一个存在值
- 当系统直接没声明直接调用一个值，会报错

dd

