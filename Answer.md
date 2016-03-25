#前端开发面试题 （答案）
- 部分转载自：http://weibo.com/920802999
- https://github.com/markyun/My-blog/tree/master/Front-end-Developer-Questions/Questions-and-Answers


## <a name='list'>目录</a>

  1. [题目](https://github.com/GabrielchenCN/Web-Front-Questions/blob/master/README.md "题目")
  1. [前言](#preface)
  1. [HTML部分](#html)
  1. [CSS部分](#css)
  1. [JavaScript部分](#js)
  1. [其他问题](#other)
  1. [对于公司的问题](#company)
  1. [前端学习网站推荐](#web)
  

<!--## <a name='questions'>答案</a>

 [答案](https://github.com/GabrielchenCN/Web-Front-Questions/blob/master/QUESTIONS.md "答案")-->
<!--## <a name='preface'>前言</a>

 [前言](https://github.com/markyun/My-blog/tree/master/Front-end-Developer-Questions "前言")-->

## <a name='html'>HTML</a>

- Doctype作用？严格模式与混杂模式如何区分？它们有何意义?

		（1）、<!DOCTYPE>声明位于位于HTML文档中的第一行，处于 <html> 标签之前。告知浏览器的解析器用什么文档标准解析这个文档。
		DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。
		（2）、标准（严格）模式的排版 和JS运作模式都是以该浏览器支持的最高标准运行。在兼容（混杂）模式中，
		页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。

- HTML5 为什么只需要写 <!DOCTYPE HTML>？

		 HTML5 不基于 SGML，因此不需要对DTD进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）;
		
		 而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型。

- 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？

		首先：CSS规范规定，每个元素都有display属性，确定该元素的类型，每个元素都有默认的display值，
		如div的display默认值为“block”，则为“块级”元素；span默认display属性值为“inline”，是“行内”元素。
		
		（1）行内元素有：a b span img input select strong（强调的语气）
		（2）块级元素有：div ul ol li dl dt dd h1 h2 h3 h4…p
		
		（3）常见的空元素：
		    <br> <hr> <img> <input> <link> <meta>
		    鲜为人知的是：
		    <area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>

- 页面导入样式时，使用link和@import有什么区别？

		（1）link属于XHTML标签，除了加载CSS外，还能用于定义RSS, 定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;
		
		（2）页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;
		
		（3）import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题;




- 常见的浏览器内核有哪些？

		 * IE浏览器的内核Trident、
		 * Mozilla的Gecko、
		 * Chrome的Blink（WebKit的分支）、
		 * Opera内核原为Presto，现为Blink;
- 常见兼容性问题？
		* png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.
		
		* 浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。
		
		* IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。
		
		  浮动ie产生的双倍距离 #box{ float:left; width:10px; margin:0 0 0 100px;}
		
		 这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入——_display:inline;
		将其转化为行内属性。(_这个符号只有ie6会识别)
		
		  渐进识别的方式，从总体中逐渐排除局部。
		
		  首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。
		  接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。
		
		  css
		      .bb{
		       background-color:#f1ee18;/*所有识别*/
		      .background-color:#00deff\9; /*IE6、7、8识别*/
		      +background-color:#a200ff;/*IE6、7识别*/
		      _background-color:#1e0bd1;/*IE6识别*/
		      }
		
		*  IE下,可以使用获取常规属性的方法来获取自定义属性,
		   也可以使用getAttribute()获取自定义属性;
		   Firefox下,只能使用getAttribute()获取自定义属性.
		   解决方法:统一通过getAttribute()获取自定义属性.
		
		* IE下,even对象有x,y属性,但是没有pageX,pageY属性;
		  Firefox下,event对象有pageX,pageY属性,但是没有x,y属性.
		
		* 解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。
		
		* Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,
		  可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决.
		
		超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了解决方法是改变CSS属性的排列顺序:
		L-V-H-A :  a:link {} a:visited {} a:hover {} a:active {}

		window.location.hash在firefox下中文自动转码为UTF-8问题
		focus()在firefox下失效的问题：由于firefox需要先blur再focus，解决方法
		setTimeout(function () {$(".app-input:eq("+id+")").focus(); }, 10);
		
		
["兼容性问题"](http://www.68design.net/Web-Guide/HTMLCSS/37154-1.html)

- html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和
HTML5?

		* HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。
		
		* 绘画 canvas
		  用于媒介回放的 video 和 audio 元素
		  本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
		  sessionStorage 的数据在浏览器关闭后自动删除
		
		  语意化更好的内容元素，比如 article、footer、header、nav、section
		  表单控件，calendar、date、time、email、url、search
		  新的技术webworker, websockt, Geolocation
		
		* 移除的元素
		
		纯表现的元素：basefont，big，center，font, s，strike，tt，u；
		
		对可用性产生负面影响的元素：frame，frameset，noframes；
		
		支持HTML5新标签：
		
		* IE8/IE7/IE6支持通过document.createElement方法产生的标签，
		  可以利用这一特性让这些浏览器支持HTML5新标签，
		
		  浏览器支持新标签后，还需要添加标签默认的样式：
		
		* 当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架
		   <!--[if lt IE 9]>
		   <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>
		   <![endif]-->
		如何区分： DOCTYPE声明\新增的结构元素\功能元素

- 举出5个HTML5的新标签并说明其意义

		<audio>标签定义音乐。 支持三种格式,ogg,mp3,wav。 
		<canvas>使用JavaScript在网页上绘制图形图像。
		<datalist> 定义选项列表.和input一起用，实现<select> <option> 类似效果不过还可以自己输入内容
		ex.
		<input id="myCar" list="cars" />
		<datalist id="cars">
		  <option value="BMW">
		  <option value="Ford">
		  <option value="Volvo">
		</datalist>
		<nav> 标记定义导航链接
		<footer> 标记定义一个页面或一个区域的底部
		<video> 标记定义一个视频
		<progress>状态标签 (任务过程:安装、加载) ,进度条效果

- 简述一下你对HTML语义化的理解？

		1.内容结构化,失去CSS样式也能有良好的结构 2.用户体验好，如alt等提示标签 3.有利于SEO（搜索引擎优化） 
		4.方便其他设备解析 5.便于团队开发和维护

- (写)描述一段语义的html代码吧。

- HTML5的离线缓存（ApplicationCache）怎么用，工作原理能不能解释一下？

		在你的页面头部像下面一样加入一个manifest的属性
		<!DOCTYPE HTML>
		<html manifest = "cache.manifest">
		...
		</html>
		
		然后把需要离线缓存在本地的文件列在一个manifest(cache.manifest)配置文件中
		CACHE MANIFEST
		#上面一句必须
		#v1.0.0
		#需要缓存的文件
		CACHE:
		a.js
		b.css
		#不需要缓存的文件
		NETWORK:
		*
		#无法访问页面
		FALLBACK:
		404.html
		
		注意：与html5本地储存不同，本地缓存是指localStorage和sessionStorage

- 浏览器是怎么对HTML5的离线储存资源进行管理和加载的呢？

		在线的情况下，浏览器发现html头部有manifest属性，它会请求manifest文件，如果是第一次访问app，
		那么浏览器就会根据manifest文件的内容下载相应的资源并且进行离线存储。如果已经访问过app并且
		资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的manifest文件
		与旧的manifest文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载
		文件中的资源并进行离线存储。
		离线的情况下，浏览器就直接使用离线存储的资源。

- 请描述一下 cookies，sessionStorage 和 localStorage 的区别？

		cookie在浏览器和服务器间来回传递。 sessionStorage和localStorage不会
		sessionStorage和localStorage的存储空间更大；
		sessionStorage和localStorage有更多丰富易用的接口；
		sessionStorage和localStorage各自独立的存储空间；

- iframe有那些缺点？

		*iframe会阻塞主页面的Onload事件；
		
		*iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
		
		使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript
		动态给iframe添加src属性值，这样可以可以绕开以上两个问题。

- Label的作用是什么？是怎么用的？（加 for）

		label标签来定义表单控制间的关系,当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。
		
		<label for="Name">Number:</label> <input type=“text“name="Name" id="Name"/> 
		
		<label>Date:<input type="text" name="B" /></label>

- HTML5的form如何关闭自动完成功能？

		给不想要提示的input是设置autocomplete=off即可

- 如何实现浏览器内多个标签页之间的通信? (阿里)

		调用localstorge、cookies等本地存储方式

- 如何使用websocket？如何兼容低浏览器？(阿里)

		在支持WebSocket的浏览器中，在创建socket之后。可以通过onopen，onmessage，onclose即onerror
		四个事件实现对socket进行响应。
		0.var ws = new WebSocket(“ws://localhost:8080”);
		申请一个WebSocket对象，参数是需要连接的服务器端的地址，同http协议使用http://开头一样，
		WebSocket协议的URL使用ws://开头，另外安全的WebSocket协议使用wss://开头。
		1.ws.send(“hello”);
		用于叫消息发送到服务端
		2.ws.onopen = function() { console.log(“open”)};
		当websocket创建成功时，即会触发onopen事件
		3.ws.onmessage = function(evt) { console.log(evt.data) };
		当客户端收到服务端发来的消息时，会触发onmessage事件，参数evt.data中包含server传输过来的数据
		4.ws.onclose = function(evt) { console.log(“WebSocketClosed!”); };
		当客户端收到服务端发送的关闭连接的请求时，触发onclose事件
		5.ws.onerror = function(evt) { console.log(“WebSocketError!”); };
		如果出现连接，处理，接收，发送数据失败的时候就会触发onerror事件

		Adobe Flash Socket 、 ActiveX HTMLFile (IE) 、 基于 multipart 编码发送 XHR 、 基于长轮询的 XHR

- 页面可见性（Page Visibility）API 可以有哪些用途？
- 页面渲染的过程？

		1.解析HTML代码并生成一个 DOM 树。
		
		2.解析CSS文件，顺序为：浏览器默认样式->自定义样式->页面内的样式。
		
		3.生成一个渲染树（render tree）。这个渲染树和DOM树的不同之处在于，它是受样式影响的。它不包括那些不可见的节点。
		
		4.当渲染树生成之后，浏览器就会在屏幕上“画”出所有渲染树中的节点。

- 什么情况下会触发浏览器的repaint/reflow?

		当 DOM 元素的属性发生变化 (如 color) 时, 浏览器会通知 render 重新描绘相应的元素, 此过程称为 repaint。
		如果该次变化涉及元素布局 (如 width), 浏览器则抛弃原有属性, 重新计算并把结果传递给 render 以重新描绘
		页面元素,此过程称为 reflow。
		1. DOM元素的添加、修改（内容）、删除( Reflow + Repaint)
		2. 仅修改DOM元素的字体颜色（只有Repaint，因为不需要调整布局）
		3. 应用新的样式或者修改任何影响元素外观的属性
		4. Resize浏览器窗口、滚动页面
		5. 读取元素的某些属性（offsetLeft、offsetTop、offsetHeight、offsetWidth、 scrollTop/Left/Width/Height、clientTop/Left/Width/Height、 getComputedStyle()、currentStyle(in IE))

[重构相关](http://www.blueidea.com/tech/web/2011/8365.asp)

## <a name='css'>CSS</a>

- 响应式设计

		1.<meta name="viewport" content="width=device-width, initial-scale=1" 		  />viewport是网页默认的宽度和高度，上面这行代码的意思是，网页宽度默认等于屏幕宽度（width=device-width），
		原始缩放比例（initial-scale=1）为1.0，即网页初始大小占屏幕面积的100%。
		2.不适用绝对宽度
		3.相对大小的字体 rem em
		4.浮动布局
		5.选择加载CSS
		6.CSS的@media规则
		7.图片的自适应（fluid image）
		8.宽高：1vh 等于1/100的视口高度。栗子：浏览器高度900px, 1 vh = 900px/100 = 9 px。同理，如果视口宽度未750， 
		1vw = 750px/100 = 7.5 px。 或使用百分比宽度
		9.vmin 和 vmax则关于视口高度和宽度两者的最小或者最大值。(即vmin =屏幕长宽小者，vmax=屏幕长宽大者)



- CSS的常用单位 

		px：pixel，像素，屏幕上显示的最小单位，用于网页设计，直观方便；
		
		pt：point，是一个标准的长度单位，1pt＝1/72英寸，用于印刷业，非常简单易用；
		
		em：即％，在CSS中，1em＝100％，是一个比率，相对于父元素字体大小，结合CSS继承关系使用，具有灵活性。
		
		rem：CSS3新标签，相对于HTML字体大小
		
		rgba：颜色
		
		vh and vw
		 
		
		

- CSS 的 Media Type 和 Media Queries 	

		媒体类型(css2:Media Type):all screen tv
		媒体特性(css3:Media Query):width height device-width /(min/max)
		<link rel="stylesheet" media="screen and (min-width:900px)" href="big.css" type="text/css" />
		<link rel="stylesheet" media="screen and (min-width:600px) and (max-width:900px)" href="style.css" type="text/css" />
	[Media](http://www.jb51.net/css/163299.html)

- CSS选择符有哪些？哪些属性可以继承？

		*   1.id选择器（ # myid）
		    2.类选择器（.myclassname）
		    3.标签选择器（div, h1, p）
		    4.相邻选择器（h1 + p）
		    5.子选择器（ul > li）
		    6.后代选择器（li a）
		    7.通配符选择器（ * ）
		    8.属性选择器（a[rel = "external"]）
		    9.伪类选择器（a: hover, li: nth - child）
		
		*   可继承的样式： font-size font-family color, UL LI DL DD DT;
 
- CSS优先级算法如何计算？ 

		 !important >内联（1000）>  id（100） > class（10） > tag（1）
		  优先级就近原则，同权重情况下样式定义最近者为准;
		
		   important 比 内联优先级高

- CSS3新增伪类有那些？

- CSS3有哪些新特性（包含哪些模块）？

		  CSS3实现圆角（border-radius:8px），阴影（box-shadow:10px），
		  对文字加特效（text-shadow、），线性渐变（gradient），旋转（transform）
		  transform:rotate(9deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);//旋转,缩放,定位,倾斜
		  增加了更多的CSS选择器  多背景 rgba 

- 如何居中div？如何居中一个浮动元素？

		绝对定位后利用负外边距（top left）和top left 50%， 		
		.center{
			width: 100px;
			height: 200px;
			/*margin: 0 auto;*/
			top: 50%;
			left: 50%;
			margin-left: -50px;
			margin-top: -100px;
			position: absolute;
			background-color: #ff0;
		} 
		浮动元素（水平）居中（关键点在利用相对定位）
		父元素和子元素同时左浮动，然后父元素相对左移动50%，再然后子元素相对右移动50%，
		或者子元素相对左移动-50%也就可以了。如此简单如此神奇。
		.box{
		    float:left;
		    position:relative;
		    left:50%;
		}
		p{
		    float:left;
		    position:relative;
		    right:50%;
		}
[CSS奇淫巧计](http://www.cnblogs.com/2050/p/3392803.html)

- 介绍一下标准的CSS的盒子模型？与低版本IE的盒子模型有什么不同的？

		标准CSS盒子模型有：border content padding margin ,其中width，height是content大小
		ie盒子模型有： border content padding margin ,其中width,height是content+border+padding大小

- display有哪些值？说明他们的作用。position的值relative和absolute定位原点是？

		  1.   
		  block 象块类型元素一样显示。
		  none 缺省值。象行内元素类型一样显示。
		  inline-block 象行内元素一样显示，但其内容象块类型元素一样显示。
		  list-item 象块类型元素一样显示，并添加样式列表标记。
		
		  2. 
		  *absolute 
		        生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。 
		
		  *fixed （老IE不支持）
		        生成绝对定位的元素，相对于浏览器窗口进行定位。 
		
		  *relative 
		        生成相对定位的元素，相对于其正常位置进行定位。 
		
		  * static  默认值。没有定位，元素出现在正常的流中
		  *（忽略 top, bottom, left, right z-index 声明）。
		
		  * inherit 规定从父元素继承 position 属性的值。

- CSS 的box-sizing属性

		box-sizing属性可以为三个值之一：content-box（default），border-box，padding-box。
		
		content-box，border和padding不计算入width之内
		
		padding-box，padding计算入width内
		
		border-box，border和padding计算入width之内（ie盒模型）
		
- CSS3 的calc()属性

	[自适应模式实现，比box-sizing更好，存在兼容性问题](http://www.w3cplus.com/css3/how-to-use-css3-calc-function.html)

- display:none;overflow：hidden;与visibility:hidden;的区别？

		CSS display:none;
		使用该属性后，HTML元素（对象）的宽度、高度等各种属性值都将“丢失”;
		visibility:hidden;
		使用该属性后，HTML元素（对象）仅仅是在视觉上看不见（完全透明），而它所占据的空间位置仍然存在，也即是说它仍具有高度、宽度等属性值。
		overflow：hidden;
		是让超出的文本隐藏，就是在设置该属性的时候他会根据你设置的宽高把多余的那部分剪切掉

- overflow的属性有哪些？

		visible	默认值。内容不会被修剪，会呈现在元素框之外。
		hidden	内容会被修剪，并且其余内容是不可见的。
		scroll	内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容。
		auto	如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容。
		inherit	规定应该从父元素继承 overflow 属性的值。



- 请解释一下CSS3的Flexbox（弹性盒布局模型）,以及适用场景？

		box-flex 属性规定框的子元素是否可伸缩其尺寸。
		能够很好实现居中，浮动，对齐，显示次序等功能，但其向下兼容不很好，只适用于现代浏览器

- 用纯CSS创建一个三角形的原理是什么？

		border的透明度+border的宽度，当border-top为透明，border-left有颜色时，在直角处形成一个45度角

- 一个满屏 品 字布局 如何设计?

			<!doctype>
			<html>
			    <head>
			        <title>test</title>
			    </head>
			    <style>
			    *{
			        margin:0;
			        padding: 0;
			    }
			    .main{
			        width:100%;
			        height: 60%;
			    }
			    .main .left, .main .right{
			        width:50%;
			        height: 100%;
			        float:left;
			        background: #a23;
			    }
			    .main .right{
			        background: #e11;
			    }
			    .clear{
			        clear:both;
			    }
			    .header{
			        height:40%;
			        background: #e33;
			        width:100%;
			    }
			    </style>
			    <body>
			        <div class="header"></div>
			        <div class="main">
			            <div class="left"></div>
			            <div class="right"></div>
			            <div class="clear"></div>
			        </div>
			        
			    </body>
			</html>

- li与li之间有看不见的空白间隔是什么原因引起的？有什么解决办法？

		同设置display：inline-block出现间歇问题，是由于空格（white-space）产生
		可通过设置父元素（ul）font-size:0，再设置本身元素字体大小解决,
		也可以利用移除空格，负margin,letter-spacing,word-spacing等解决。

- 经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用hack的技巧 ？

- 为什么要初始化CSS样式。

- absolute的containing block计算方式跟正常流有什么不同？

- CSS里的visibility属性有个collapse属性值是干嘛用的？在不同浏览器下以后什么区别？

		一般不使用，推荐不使用，在chrome上对于table等元素作用和hidden一样，
		但在火狐上作用和display：none一样（所占据位置也会消失）

- position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样？

- 对BFC规范的理解？

- CSS权重优先级是如何计算的？

以下是权重的规则：标签的权重为1，class的权重为10，id的权重为100，以下例子是演示各种定义的权重值：

		/*权重为1*/
		div{
		}
		/*权重为10*/
		.class1{
		}
		/*权重为100*/
		#id1{
		}
		/*权重为100+1=101*/
		#id1 div{
		}
		/*权重为10+1=11*/
		.class1 div{
		}
		/*权重为10+10+1=21*/
		.class1 .class2 div{
		}
		内联样式权重1000
		如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现

- 请解释一下浮动和它的工作原理？清除浮动的技巧

- 移动端的布局用过媒体查询吗？

- 使用 CSS 预处理器吗？喜欢那个，Why？

- CSS优化、提高性能的方法有哪些？

- CSS图片优化

		  CSS Sprites   多张小图片组合成一张大图片，一次请求即可
		  CSS icon font 图片icon像文字一样可配置
		  base64        通过对图片编码，引用图片
				1.减少了HTTP请求
				2.某些文件可以避免跨域的问题
				3.没有图片更新要重新上传，还要清理缓存的问题
				不足在于：1.浏览器支持 2.增加了CSS文件的尺寸 3.编码成本

- 浏览器是怎样解析CSS选择器的？

- 在网页中的应该使用奇数还是偶数的字体？为什么呢？

- margin和padding分别适合什么场景使用？

- 元素竖向的百分比设定是相对于容器的高度吗？

- 全屏滚动的原理是什么？用到了CSS的那些属性？

- 什么是响应式设计？响应式设计的基本原理是什么？如何兼容低版本的IE？

- 视差滚动效果，如何给每页做不同的动画？（回到顶部，向下滑动要再次出现，和只出现一次分别怎么做？）

- ::before 和 :after中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用。

- 如何修改chrome记住密码后自动填充表单的黄色背景 ？

- 你对line-height是如何理解的？

- 设置元素浮动后，该元素的display值是多少？（自动变成display:block）

- 怎么让Chrome支持小于12px 的文字？

- 让页面里的字体变清晰，变细用CSS怎么做？（-webkit-font-smoothing: antialiased;）

- font-style属性可以让它赋值为“oblique” oblique是什么意思？

- position:fixed;在android下无效怎么处理？

- 如果需要手动写动画，你认为最小时间间隔是多久，为什么？（阿里）

- display:inline-block 什么时候会显示间隙？(携程)

- display:inline-block 兼容IE的hack(美的)

		div {display:inline-block;*display:inline; *zoom:1;...} 

- overflow: scroll时不能平滑滚动的问题怎么处理？

- overflow: auto时页面进度条出现后页面不跳动？

		CSS3计算calc和vw单位巧妙实现滚动条出现页面不跳动
		很简单，只要一行代码就搞定了：
		.wrap-outer {
		    margin-left: calc(100vw - 100%);
		}
		或者：
		.wrap-outer {
		    padding-left: calc(100vw - 100%);
		}
		然后就可以庆祝放鞭炮啦！！
		
		首先，.wrap-outer指的是居中定宽主体的父级，如果没有，创建一个
		（使用主体也是可以实现类似效果，不过本着宽度分离原则，不推荐）；
		
		然后，calc是CSS3中的计算，IE10+浏览器支持，IE9浏览器基本支持
		(不能用在background-position上)；
		
		最后，100vw相对于浏览器的window.innerWidth，是浏览器的内部宽度，
		注意，滚动条宽度也计算在内！而100%是可用宽度，是不含滚动条的宽度。
		于是，calc(100vw - 100%)就是浏览器滚动条的宽度大小（如果有，如
		果没有滚动条则是0）！左右都有一个滚动条宽度（或都是0）被占用，
		主体内容就可以永远居中浏览器啦，从而没有任何跳动！
[demo](http://www.zhangxinxu.com/study/201501/body-scrollbar-no-jump.html "demo")
支持：IE9+以及其他现代浏览器。
[原作者](http://www.zhangxinxu.com/wordpress/?p=4552 "原作者")

- 自适应布局怎么编写？

	[自适应网页设计](http://www.ruanyifeng.com/blog/2012/05/responsive_web_design.html "自适应")
	
- 什么是Cookie 隔离？（或者说：请求资源的时候不要让它带cookie怎么做）

		如果静态文件都放在主域名下，那静态文件请求的时候都带有的cookie的数据提交给server的，非常浪费流量，
		所以不如隔离开。
		
		因为cookie有域的限制，因此不能跨域提交请求，故使用非主要域名的时候，请求头中就不会带有cookie数据，
		这样可以降低请求头的大小，降低请求时间，从而达到降低整体请求延时的目的。
		
		同时这种方式不会将cookie传入Web Server，也减少了Web Server对cookie的处理分析环节，
		提高了webserver的http请求的解析速度。
		

## <a name='js'>JavaScript</a>

-  用原生JavaScript的实现过什么功能吗？

		javascript原生操作dom方法
		    var createNode = document.createElement("div");
		    var createTextNode = document.createTextNode("hello world");
		    createNode.appendChild(createTextNode);
		    document.body.appendChild(createNode);
		    document.documentElement.appendChild(createNode);
		    //插入
		    document.body.insertBefore(createNode,div1);
		   //替换元素
		   var replaceChild = document.body.replaceChild(createNode,div1);
		   /删除元素
		    var removeChild = document.body.removeChild(div1);
		    //克隆元素
		    someNode.cloneNode(true):深度克隆，会复制节点及整个子节点
		    someNode.cloneNode(false):浅克隆，会复制节点，但不复制子节点 
	[JavaScript操作dom](http://www.2cto.com/kf/201410/347047.html)
	
		div拖拽
		对元素绑定mousedown，mousemove，mouseup事件
		在mousedown时计算
		x = e.clientX - el.offsetWidth,//鼠标指针向对于浏览器页面（或客户区）的水平坐标 - 元素的宽
		y = e.clientY - el.offsetHeight;//既当前高度差
		在mousemove的时候设定高度，
		 els.width = els.width;
		els.height = e.clientY - y + 'px'; //当前高度
		up的时候解绑
		
	[JavaScript算法实现](http://www.108js.com/index5.html)

-  用JavaScript实现私有成员。

		function Person(n, a){
		    // public
		    this.name = n;
		    // private
		    var age = a;
		    this.getName = function(){
		        return this.name;
		    }
		    this.getAge = function(){
		        return age;
		    }
		};var p =new Person("chen","21"); p.name ;p.age;
		//私有属性 不能直接访问，只能用公用方法getAge访问，而公用属性可以直接p.name访问

-  JavaScript 实现数组去重   

		//IE8+ 兼容
		function unique(arr) {
		  var ret = []
		 
		  for (var i = 0; i < arr.length; i++) {
		    var item = arr[i]
		    if (ret.indexOf(item) === -1) {
		      ret.push(item)
		    }
		  }
		 
		  return ret
		}
	[数组去重](http://blog.jobbole.com/33099/)

-  介绍JavaScript的基本数据类型。

		基本类型（sbnun）
		1.string
		2.boolean
		3.null
		4.undefined
		5.number
		
		引用数据类型(typeof只返回这两种)
		Object
		Function
		等
	[JavaScript数据类型](http://www.cnblogs.com/top5/archive/2012/03/20/2408330.html)

- 介绍JavaScript的执行上下文

		我们总结一下，在“准备工作”中完成了哪些工作：
		
		变量、函数表达式——变量声明，默认赋值为undefined；
		this——赋值；
		函数声明——赋值；
		这三种数据的准备情况我们称之为“执行上下文”或者“执行上下文环境”。

	[JavaScript执行上下文](http://www.cnblogs.com/wangfupeng1988/p/3986420.html)

-介绍JavaScript的this

		在函数中this到底取何值，是在函数真正被调用执行的时候确定的，函数定义的时候确定不了。因为this的取值是执行上下文环境的一部分，每次调用函数，都会产生一个新的执行上下文环境。

	[JavaScript的this](http://www.cnblogs.com/wangfupeng1988/p/3988422.html)
	[JavaScript的this](http://www.cnblogs.com/wangfupeng1988/p/3996037.html)

-介绍JavaScript的自由变量和作用域

		自由变量：在A作用域中使用的变量x，却没有在A作用域中声明（即在其他作用域中声明的），对于A作用域来说，x就是一个自由变量
				var x = 10 ;
				function fn(){
					 var a= 20;
					 console.log(x+a);
				}
		
		作用域：
		有人说过要到父作用域中取，其实有时候这种解释会产生歧义.
		相比而言，用这句话描述会更加贴切——要到创建这个函数的那个作用域中取值——是“创建”，
		而不是“调用”，切记切记——其实这就是所谓的“静态作用域”。
				var x = 10 ;
				function fn(){
				 console.log(x);
				}
				function show(x){
				 var x = 20;
				 (function(){
				 	fn();
				 })();
				}
				show(fn)

-  说说写JavaScript的基本规范？

-  请解释一下JavaScript原型(prototype)? 每个JS对象都有原型属性吗？

		在JavaScript 中，每当定义一个对象（函数）时候，对象中都会包含一些预定义的属性。其中函数对象的一个属性就是原型对象 prototype。注：普通对象没有prototype,但有__proto__属性。
		JS在创建对象（不论是普通对象还是函数对象）的时候，都有一个叫做__proto__的内置属性，用于指向创建它的函数对象的原型对象prototype。以上面的例子为例：
	[原型链理解1](http://www.108js.com/article/article1/10201.html?id=1092)
	[原型链理解2](http://rockyuse.iteye.com/blog/1426510)

-  JavaScript有几种类型值？（堆：原始值和 栈：引用值），你能画一下他们的内存图吗？

-  Javascript如何实现继承？

		原型链和构造器
		<script type="text/javascript">
		//组合继承
			var Person = function(name){
				this.name = name;
			}
			Person.prototype.getName = function(){
				return this.name
			}
		
			var Student = function(name,age){
				this.age=age;
				Person.call(this,name);
		
				this.setAge=function(age){
					this.age=age;
				}
			}
		
			Person.prototype.setName =function(name){
			    this.name =name;
			}
		
			/*Student.prototype.setAge =function(age){
				this.age=age;
			    不可以使用原型链寻找到age参数，因为student的原型person里没有age
			}*/
		
			Student.prototype = new Person(name);
			var p = new Person("chen");
			var s =new Student("siming","19");
			console.log(p);
			console.log(s);
			console.log(s.getName());
			console.log(s.setAge("11"));
			console.log(s.setName("sm"));
			console.log(p);
			console.log(s);
		
		</script>
	[多种方式实现继承](http://www.cnblogs.com/xieex/archive/2008/01/25/1053342.html)
 
 
-  JavaScript函数式编程

		1. 函数是"第一等公民"
		2. 只用"表达式"，不用"语句"
		3. 没有"副作用"
		4. 不修改状态
		5. 引用透明
	[函数式编程](http://www.ruanyifeng.com/blog/2012/04/functional_programming.html)

-  event.target与event.currentTarget 的含义和区别
  
		target	返回触发此事件的元素（事件的目标节点）。
		（event.target 属性在实现事件代理时会被用到。）
		currentTarget	返回其事件监听器触发该事件的元素
		（该属性总是指向被绑定事件处理器的元素，将同一个事件处理器绑定到多个元素）。
		对于IE8及其以下均要做兼容处理

-  解释一下Javascript的事件代理？
 		
 	 		核心思想（实现机制）是 事件冒泡(Event Bubble) 
			事件代理（Event Delegation），又称之为事件委托。是 JavaScript 中常用绑定事件的常用技巧。
			
			顾名思义，“事件代理”即是把原本需要绑定的事件委托给父元素，让父元素担当事件监听的职务。
			
			DOM操作是十分消耗性能的。所以重复的事件绑定简直是性能杀手。
			
			而事件代理的核心思想，就是通过尽量少的绑定，去监听尽量多的事件。

-  如何创建一个对象? （画出此对象的内存图）

-  谈谈This对象的理解。

-  eval是做什么的？

		它的功能是把对应的字符串解析成JS代码并运行；
		应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。

-  什么是window对象? 什么是document对象?

		BOM and DOM

-  null，undefined的区别？

		null
		
		这是一个对象，但是为空。因为是对象，所以 typeof null 返回 'object' 。
		
		null 是 JavaScript 保留关键字。
		
		null 参与数值运算时其值会自动转换为 0 ，因此，下列表达式计算后会得到正确的数值：
		
		表达式：123 + null　　　　结果值：123
		
		表达式：123 * null　　　　结果值：0
		
		undefined
		
		undefined是全局对象（window）的一个特殊属性，其值是未定义的。但 typeof undefined 返回 'undefined' 。
		
		虽然undefined是有特殊含义的，但它确实是一个属性，而且是全局对象（window）的属性。

	[null，undefined的区别](http://www.ruanyifeng.com/blog/2014/03/undefined-vs-null.html)
	[null，undefined的区别 比较好](http://www.nowamagic.net/librarys/veda/detail/1201)

-  用过typeOf 和 instanceOf吗？ 说说他们的区别

		 typeof用以获取一个变量或者表达式的类型，typeof一般只能返回如下几个结果：
		
		number,boolean,string,undefined,function（函数）,object（NULL,数组，对象）。
		
		正因为typeof遇到null,数组,对象时都会返回object类型，所以当我们要判断一个对象是否是数组时
		
		或者判断某个变量是否是某个对象的实例则要选择使用另一个关键语法instanceof
		
		instanceof用于判断一个变量是否某个对象的实例，如var a=new Array();alert(a instanceof Array);会返回true.
		
		instanceof判断规则：
		Instanceof运算符的第一个变量是一个对象，暂时称为A；第二个变量一般是一个函数，暂时称为B。

		Instanceof的判断队则是：沿着A的__proto__这条线来找，同时沿着B的prototype这条线来找，如果两条线能找到同一个引用，即同一个对象，那么就返回true。如果找到终点还未重合，则返回false。

-  如何判断对象是不是Function?

		function isFunction(obj) {  
		
		  return Object.prototype.toString.call(obj) === '[object Function]';   
		
		};
		解释：ECMA规范定义了Object.prototype.toString的行为：首先，取得对象的一个内部属性[[Class]]，
		然后依据这个属性，返回一个类似于"[object Array]"的字符串作为结果（看过ECMA标准的应该都知道，
		[[]]用来表示语言内部用到的、外部不可直接访问的属性，称为“内部属性”）。利用这个方法，再配合call
		，我们可以取得任何对象的内部属性[[Class]]，然后把类型检测转化为字符串比较，以达到我们的目的
		；call改变toString的this引用为待检测的对象，返回此对象的字符串表示，然后对比此字符串是否是
		'[object Array]'，以判断其是否是Array的实例。也许你要问了，为什么不直接o.toString()？嗯，虽
		然Array继承自Object，也会有toString方法，但是这个方法有可能会被改写而达不到我们的要求，
		而Object.prototype则是老虎的屁股，很少有人敢去碰它的，所以能一定程度保证其“纯洁性”：）


-  href="javascript:; onclick="javascript:return false;" 这样写的作用是什么？

		href="javascript:;" 阻止浏览器默认操作
		
		onclick="javascript:return false;" 修复IE6下的BUG
		其中javascript是一个伪协议
		注意，虽然这么做是可行的，但利用 javascript: 伪协议来执行JavaScript代码是不推荐的，
		推荐的做法是为链接元素绑定 click 事件。

- What exactly is the difference between undefined and  void 0 ?

		The difference is that some browsers allow you to overwrite the value of undefined.(现代浏览器不允许这样做) 
		However, void(anything) always returns real undefined.
		
		undefined = 1;
		console.log(!!undefined); //true
		console.log(!!void(0)); //false
		
- JavaScript的stopImmediatePropagation 与 stopPropagation 不同之处

<button onclick="console.log('target')">CLICK ME</button>

		document.addEventListener('click', function(e) {
		    console.log('bubble');
		});
		
		document.addEventListener('click', function(e) {
		    console.log('capture');
		    //e.stopImmediatePropagation();
		}, true);
	[代码](http://jsfiddle.net/FsJgb/)
		请看文档里对event.stopImmediatePropagation()的描述：
		
		Keeps the rest of the handlers from being executed and prevents the event from bubbling up the DOM tree.
		从这里可以看出，stopImmediatePropagation做了两件事情：
		第一件事：阻止 绑定在事件触发元素的 其他同类事件的callback的运行，看他下面的例子就很明白：
		
		$("p").click(function(event) {
		  event.stopImmediatePropagation();
		});
		$("p").click(function(event) {
		  // 不会执行以下代码
		  $(this).css("background-color", "#f00");
		});
		第二件事，阻止事件传播到父元素，这跟stopPropagation的作用是一样的。
		
		所以文档里面还有这么一句话：
		
		.. this method also stops the bubbling by implicitly calling event.stopPropagation().
		意思是说其实这个方法是调用了stopPropagation()方法的。
		
		stopImmediatePropagation比stopPropagation多做了第一件事情，这就是他们之间的区别
				
-  写一个通用的事件侦听器函数(机试题)。

		       // event(事件)工具集，来源：github.com/markyun
		       markyun.Event = {
		           // 页面加载完成后
		           readyEvent : function(fn) {
		               if (fn==null) {
		                   fn=document;
		               }
		               var oldonload = window.onload;
		               if (typeof window.onload != 'function') {
		                   window.onload = fn;
		               } else {
		                   window.onload = function() {
		                       oldonload();
		                       fn();
		                   };
		               }
		           },
		           // 视能力分别使用dom0||dom2||IE方式 来绑定事件
		           // 参数： 操作的元素,事件名称 ,事件处理程序
		           addEvent : function(element, type, handler) {
		               if (element.addEventListener) {
		                   //事件类型、需要执行的函数、是否捕捉
		                   element.addEventListener(type, handler, false);
		               } else if (element.attachEvent) {
		                   element.attachEvent('on' + type, function() {
		                       handler.call(element);
		                   });
		               } else {
		                   element['on' + type] = handler;
		               }
		           },
		           // 移除事件
		           removeEvent : function(element, type, handler) {
		               if (element.removeEventListener) {
		                   element.removeEventListener(type, handler, false);
		               } else if (element.datachEvent) {
		                   element.detachEvent('on' + type, handler);
		               } else {
		                   element['on' + type] = null;
		               }
		           },
		           // 阻止事件 (主要是事件冒泡，因为IE不支持事件捕获)
		           stopPropagation : function(ev) {
		               if (ev.stopPropagation) {
		                   ev.stopPropagation();
		               } else {
		                   ev.cancelBubble = true;
		               }
		           },
		           // 取消事件的默认行为
		           preventDefault : function(event) {
		               if (event.preventDefault) {
		                   event.preventDefault();
		               } else {
		                   event.returnValue = false;
		               }
		           },
		           // 获取事件目标
		           getTarget : function(event) {
		               return event.target || event.srcElement;
		           },
		           // 获取event对象的引用，取到事件的所有信息，确保随时能使用event；
		           getEvent : function(e) {
		               var ev = e || window.event;
		               if (!ev) {
		                   var c = this.getEvent.caller;
		                   while (c) {
		                       ev = c.arguments[0];
		                       if (ev && Event == ev.constructor) {
		                           break;
		                       }
		                       c = c.caller;
		                   }
		               }
		               return ev;
		           }
		       }


-  关于事件，IE与火狐的事件机制有什么区别？ 如何阻止冒泡？

		IE：
		默认事件为冒泡事件attachEvent()
	
		window.event.cancelBubble = true;//停止冒泡
		window.event.returnValue = false;//阻止事件的默认行为
		
		Firefox：
		通过	addEventListener(event,fn,useCapture) 中useCapture设置冒泡或者是捕获事件//false为冒泡，比较兼容
		event.preventDefault();// 取消事件的默认行为 
		event.stopPropagation(); // 阻止事件的传播
		
		事件冒泡：事件按照从最特定的事件目标到最不特定的事件目标(document对象)的顺序触发，即子级元素先触发，父级元素后触发。
		假设一个元素div，它有一个下级元素p。
		<div>
		　　<p>元素</p>
		</div>
		这两个元素都绑定了click事件，如果用户点击了p，它在div和p上都触发了click事件。p先触发，div后触发。这就叫做事件冒泡。
		
		事件捕获
		当你使用事件捕获时，父级元素先触发，子级元素后触发，即div先触发，p后触发。


-  什么是闭包（closure），为什么要用它？

		解决从外部读取函数内部变量的问题，因为JavaScript的作用域是函数作用域
		且查找变量的方式是从内往外查找（"链式作用域"结构chain scope）。
		闭包就是能够读取其他函数内部变量的函数。
		用途：一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。
		使用闭包的注意点
		1）由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，
		否则会造成网页的性能问题，在IE中可能导致内存泄露。
		解决方法是，在退出函数之前，将不使用的局部变量全部删除。
		2）闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，
		把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（privatevalue），这时
		一定要小心，不要随便改变父函数内部变量的值。


-  "use strict";是什么意思 ? 使用它的有什么好处或坏处？

	
		1.全局变量显式声明
		2.静态绑定
		3.增强的安全措施
		4.重名错误
		5.保留字 ES6
	[USE STRICT ](http://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html)
	
-  ["1", "2", "3"].map(parseInt) 答案是多少？

		[1,NaN,NaN]
		因为 parseInt 需要两个参数 (val, radix)，其中 radix 表示解析时用的基数。map 传了 3 个 (element, index, array)，对应的 radix 不合法导致解析失败
		
	[解析](http://blog.csdn.net/freshlover/article/details/19034079 "解析")
	
-  如何判断一个对象是否属于某个类？

		A instanceof B

-  new操作符具体干了什么呢?

		1、创建一个新对象；[var o = new Object();]
		
		2、将构造函数的作用域赋给新对象（因此this指向了这个新对象）；[Person.apply(o)]  [Person原来的this指向的是window]
		
		3、执行构造函数中的代码(为这个新对象添加属性)；
		
		4、返回新对象。

-  Javascript中，有一个函数，执行时对象查找时，永远不会去查找原型，这个函数是？

		hasOwnProperty 只会查找对象本身的属性（用for in 遍历属性的时候经常使用）

-  JavaScript中的arguments 和arguments.callee

		arguments 是一个类数组对象。代表传给一个function的参数列表。arguments 对象是函数内部的本地变量；arguments 已经不再是函数的属性了。
		
		arguments对象中有一个非常有用的属性：callee。arguments.callee返回此arguments对象所在的当前函数引用。在使用函数递归调用时推荐使用arguments.callee代替函数名本身。
		
		由JavaScript中函数的声明和调用特性，可以看出JavaScript中函数是不能重载的。
		
		根据其他语言中重载的依据："函数返回值不同或形参个数不同"，我们可以得出上述结论：
		
		第一：Javascript函数的声明是没有返回值类型这一说法的；
		
		第二：JavaScript中形参的个数严格意义上来讲只是为了方便在函数中的变量操作，实际上实参已经存储在arguments对象中了。
		
		另外，从JavaScript函数本身深入理解为什么JavaScript中函数是不能重载的：在JavaScript中，函数其实也是对象，函数名是关于函数的引用，或者说函数名本身就是变量。对于如下所示的函数声明与函数表达式，其实含以上是一样的（在不考虑函数声明与函数表达式区别的前提下），非常有利于我们理解JavaScript中函数是不能重载的这一特性。
		
		注意：严格模式下，callee不可用

-  对JSON的了解？

-  `[].forEach.call($$("*"),function(a){
  a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16)
})` 能解释一下这段代码的意思吗？

-  js延迟加载的方式有哪些？

-  ajax是什么，解释一下它的工作原理?

	async javascript and xml

-  同步和异步的区别?

-  如何解决跨域问题?

			    1.jsonp 需要目标服务器配合一个callback函数。
			
			　　2.window.name+iframe 需要目标服务器响应window.name。
			
			　　3.window.location.hash+iframe 同样需要目标服务器作处理。
			
			　　4.html5的 postMessage+ifrme 这个也是需要目标服务器或者说是目标页面写一个postMessage，主要侧重于前端通讯。
			
			　　5.CORS  需要服务器设置header ：Access-Control-Allow-Origin。
			
			　　6.nginx反向代理 这个方法一般很少有人提及，但是他可以不用目标服务器配合，不过需要你搭建一个中转nginx服务器，用于转发请求。

-  URIError: URI malformed 是什么原因？
		URL格式错误，一般是由于编码错误或编码格式不一致导致
		JavaScript有三个编码函数和三个解码函数，它们应该一一对应
		escape,encodeURI,encodeURIComponent，相应3个解码函数：unescape,decodeURI,decodeURIComponent
		1.encodeURI() 函数可把字符串作为 URI 进行编码。该方法不会对 ASCII 字母和数字进行编码，
		也不会对这些 ASCII 标点符号进行编码： - _ . ! ~ * ' ( ) 。
		
		2.escape:该方法不会对 ASCII 字母和数字进行编码，也不会对下面这些 ASCII 标点符号进行编码： * @ - _ + . / 。其他所有的字符都会被转义序列替换。
		
		3.如果 URI 组件中含有分隔符，比如 ? 和 #，则应当使用 encodeURIComponent() 方法分别对各组件进行编码。


-  JS模块化开发怎么做？

		[ 立即执行函数](http://www.ruanyifeng.com/blog/2012/10/javascript_module.html),不暴露私有成员
		
		        var module1 = (function(){
		        　　　　var _count = 0;
		        　　　　var m1 = function(){
		        　　　　　　//...
		        　　　　};
		        　　　　var m2 = function(){
		        　　　　　　//...
		        　　　　};
		        　　　　return {
		        　　　　　　m1 : m1,
		        　　　　　　m2 : m2
		        　　　　};
		        　　})();
		 使用立即执行函数避免变量污染

-  requireJS的核心原理是什么？（如何动态加载的？如何避免多次加载的？如何
缓存的？）

-  谈一谈你对ECMAScript6的了解？

-  ECMAScript6 怎么写class么，为什么会出现class这种东西? 

-  AMD（Modules/Asynchronous-Definition）、CMD（Common Module Definition）规范区别？

		1. 对于依赖的模块，AMD 是提前执行，CMD 是延迟执行。不过 RequireJS 从 2.0 开始，也改成可以延迟执行（根据写法不同，处理方式不同）。CMD 推崇 as lazy as possible.
		2. CMD 推崇依赖就近，AMD 推崇依赖前置。
		3. AMD 的 API 默认是一个当多个用，CMD 的 API 严格区分，推崇职责单一。比如 AMD 里，require 分全局 require 和局部 require，都叫 require。CMD 里，没有全局 require，而是根据模块系统的完备性，提供 seajs.use 来实现模块系统的加载启动。CMD 里，每个 API 都简单纯粹。
		4.知乎 CMD 作者玉伯回答
[详解见评论](http://www.zhihu.com/question/20351507/answer/14859415) 

-  异步加载的方式有哪些？

-  .call() 和 .apply() 的区别？

		 call 的第二个参数可以是任意类型，而apply的第二个参数必须是数组


-  JavaScript中的作用域与变量声明提升？

-  如何编写高性能的Javascript？

-  那些操作会造成内存泄漏？

-  JQuery的源码看过吗？能不能简单概况一下它的实现原理？
-  JQuery为什么要使用$（美元符号）？

		$是对jQuery的一个引用，$()=jQuery();避免了变量冲突
		如果其他库也使用了$定义变量会产生冲突，可用var $j = JQuery.noConflict();重新定义别名

-  jQuery.fn的init方法返回的this指的是什么对象？为什么要返回this？

-  jquery中如何将数组转化为json字符串，然后再转化回来？

-  jQuery 的属性拷贝(extend)的实现原理是什么，如何实现深拷贝？ 

-  jquery.extend 与 jquery.fn.extend的区别？
		从jQuery的源码中可以看到，jQuery.extend和jQuery.fn.extend其实是同指向同一方法的不同引用
		
		jQuery.extend = jQuery.fn.extend = function() {
		jQuery.extend 对jQuery本身的属性和方法进行了扩展
		
		jQuery.fn.extend 对jQuery.fn的属性和方法进行了扩展
		通过extend()函数可以方便快速的扩展功能，不会破坏jQuery的原型结构
		
		jQuery.extend = jQuery.fn.extend = function(){...}; 这个是连等，也就是2个指向同一个函数，怎么会实现不同的功能呢？这就是this 力量了！
		
		针对fn与jQuery其实是2个不同的对象，在之前有讲述：
		
		jQuery.extend 调用的时候，this是指向jQuery对象的(jQuery是函数，也是对象！)，所以这里扩展在jQuery上。
		而jQuery.fn.extend 调用的时候，this指向fn对象，jQuery.fn 和jQuery.prototype指向同一对象，扩展fn就是扩展jQuery.prototype原型对象。
		这里增加的是原型方法，也就是对象方法了。所以jQuery的api中提供了以上2中扩展函数。

-  jQuery 的队列是如何实现的？队列可以用在哪些地方？

-  谈一下Jquery中的bind(),live(),delegate(),on()的区别？
-  JQuery的deferred怎么用，解决了什么问题？

		使用方法：1.ajax操作的链式写法
		    $.ajax("test.html")
		
		　　.done(function(){ alert("哈哈，成功了！"); })
		
		　　.fail(function(){ alert("出错啦！"); });
		　　2.指定同一操作的多个回调函数
		　　$.ajax("test.html")
		
		　　.done(function(){ alert("哈哈，成功了！");} )
		
		　　.fail(function(){ alert("出错啦！"); } )
		
		　　.done(function(){ alert("第二个回调函数！");} );
		　　3.为多个操作指定回调函数
		　　　　$.when($.ajax("test1.html"), $.ajax("test2.html"))
		
		　　.done(function(){ alert("哈哈，成功了！"); })
		
		　　.fail(function(){ alert("出错啦！"); });
[deferred详解](http://www.jb51.net/article/28054.htm)

-  JQuery一个对象可以同时绑定多个事件，这是如何实现的？

-  jQuery 是通过哪个方法和 Sizzle 选择器结合的？（jQuery.fn.find()进入Sizzle）

-  针对 jQuery性能的优化方法？

-  Jquery与jQuery UI有啥区别？

-  jQuery和Zepto的区别？各自的使用场景？

-  Zepto的点透问题如何解决？

-  jQueryUI如何自定义组件?

-  需求：实现一个页面操作不会整页刷新的网站，并且能在浏览器前进、后退时正确响应。给出你的技术实现方案？

-  如何判断当前脚本运行在浏览器还是node环境中？（阿里）

-  移动端最小触控区域是多大？

-  jQuery 的 slideUp动画 ，如果目标元素是被外部事件驱动, 当鼠标快速地连续触发外部元素事件, 动画会滞后的反复执行，该如何处理呢?
-  把 Script 标签 放在页面的最底部的body封闭之前 和封闭之后有什么区别？浏览器会如何解析它们？

-  移动端的点击事件的有延迟，时间是多久，为什么会有？ 怎么解决这个延时？（click 有 300ms 延迟,为了实现safari的双击事件的设计，浏览器要知道你是不是要双击操作。）

-  知道各种JS框架(Angular, Backbone, Ember, React, Meteor, Knockout...)么? 能讲出他们各自的优点和缺点么?
-  Underscore 对哪些 JS 原生对象进行了扩展以及提供了哪些好用的函数方法？
-  angularJS的双向绑定是如何实现的（它的原理是什么）？
		angular并不存在定时脏检测。
		angular对常用的dom事件，xhr事件等做了封装， 在里面触发进入angular的digest流程。
		在digest流程里面， 会从rootscope开始遍历， 检查所有的watcher。
		
		angular性能优化心得
		谈起angular的脏检查机制(dirty-checking), 常见的误解就是认为： ng是定时轮询去检查model是否变更。
		其实，ng只有在指定事件触发后，才进入$digest cycle：
		DOM事件，譬如用户输入文本，点击按钮等。(ng-click)
		XHR响应事件 ($http)
		浏览器Location变更事件 ($location)
		Timer事件($timeout, $interval)
		执行$digest()或$apply()
[知乎](http://www.zhihu.com/question/23275373 "知乎")
		  
   

-  Node.js的适用场景？

-  (如果会用node)知道route, middleware, cluster, nodemon, pm2, server-side rendering么?
-  解释一下 Backbone 的 MVC 实现方式？

-  什么是“前端路由”?什么时候适合使用“前端路由”? “前端路由”有哪些优点和缺点?

-  知道什么是webkit么? 知道怎么用浏览器的各种工具来调试和debug代码么?

- 如何测试前端代码么? 知道BDD, TDD, Unit Test么? 知道怎么测试你的前端工程么(mocha, sinon, jasmin, qUnit..)?

		GUI测试
		js测试 
	[qUnit官网](http://qunitjs.com/) jquery团队开发 	
	[qUnit讲解DEMO](http://www.zhangxinxu.com/wordpress/2013/04/qunit-javascript-unit-test-%E5%8D%95%E5%85%83%E6%B5%8B%E8%AF%95/)
	[前端测试](https://www.zhihu.com/question/29922082)

- 前端templating(Mustache, underscore, handlebars)是干嘛的, 怎么用?

- 简述一下 Handlebars 的基本用法？

- 简述一下 Handlerbars 的对模板的基本处理流程， 如何编译的？如何缓存的？
- 阅读javascript代码,输出是什么？

		    a(); // a
		    b(); //缺少对象 Uncaught TypeError: b is not a function
		    function a(){
		        alert('a');
		    }
		 
		    var b= function(){
		        alert('b');
		    }
		    
		    说明a() 被预先装载

- 阅读javascript代码，回答问题(是否通过f取到a和b，如果可以那怎么获取，如果不可以请说出原因)
 
		var F = function(){};
		Object.prototype.a = function(){};
		Function.prototype.b = function(){};
		var f = new F();

		f.a === Object.prototype.a   //=> true
		f.b === Function.prototype.b  //=> false
		f 的原型链：
		
		f -----> F.prototype -----> Object.prototype -----> null
		F 的原型链：
		
		F -----> Function.prototype -----> Object.prototype -----> null
		所以
		f(F的实例对象)能访问a
		F(函数对象)能访问a,b

- 阅读javascript代码，回答问题(输出是什么，为什么？)

		var a = {n: 1}                 
		var b = a;
		a.x = a = {n: 2}
		console.log(a.x);//undefined
		console.log(b.x);/{n:2}
		
		
		//自己都说不通了。。
		第一、二行表示a\b 同时指向{n:1}
		第三行 表达式解析为  a.x = (a = {n: 2})
		执行顺序是左到右，所以有
		a.x=Expression 时，a={n:1} ---->{n:1}.x=Expression，此处是{n:1}内存块被赋值了x
		执行a = {n: 2}时，aa被〈重新定义〉指向到 {n: 2}，此时b=a，也被指向{n:2};
		console.log(a.x);时 a={n: 2} 不是{n:1} 所以没有.x属性 ,a.x 未定义
		console.log(b.x);时 a={n: 2} b是a的引用，没有被重新定义，b.x指向{n：2};

		解释
		var a,b,c,d;  
		a=b=c=d={a:1};  
		a.x=a=b.y=b=c.z=c={}  
		console.log(a,b,c,d) 
[详解见评论](http://www.iteye.com/topic/785445 "详解见评论")

- javascript 深复制和浅复制

		js中的赋值都为引用传递.就是说,在把一个对像赋值给一个变量时,那么这个变量所指向的仍就是原来对像的地址.引用就是浅拷贝。
		深拷贝就是不紧复制对象的基本类,同时也复制原对象中的对象.就是说完全是新对象产生的，新对象所指向的不是原来对像的地址。
		jquery中用 $.extend(true, {}, ...)
		[深复制实现](http://jerryzou.com/posts/dive-into-deep-clone-in-javascript/)

- 阅读javascript代码，回答问题(输出是什么，为什么？)
	
		var obj={1:'a',2:'b',length:2,push:[].push} ;
		obj.push('c');
		
		console.log(obj[2]); //c
		console.log(obj.length); //3
		if var obj={1:'a',2:'b',length:3,push:[].push} ;
		how about your answer?
		console.log(obj[2]); //b
		console.log(obj.length); //4
                ps：我不是很明白为什么是这个结果

- JavaScript实现 add(1)(2)(3)
		
		var add = function(a){
		    return function(b){
		        return function(c){
		            return a+b+c;
		        };
		    };
		};
		 
		add(1)(2)(3); //6
		//有问题
		function add(x) {
		    var sum = x;
		    var tmp = function (y) {
		        sum = sum + y;
		        return tmp;
		    };
		    tmp.toString = function () {
		        return sum;
		    };
		    return tmp;
		}
		console.log(add(1)(2)(3));  //6
		console.log(add(1)(2)(3)(4));   //10

- 已知
  var Person = function(name){
		this.name = name;
	}
	Person.prototype.getName = function(){
		return this.name
	}
   从Person中继承一个Student(name,age)类，并实现setAge 和setName方法

		var Student = function(name,age){
				this.age=age;
				Person.call(this,name);
		
				this.setAge=function(age){
					this.age=age;
				}
			}
		
			Person.prototype.setName =function(name){
			    this.name =name;
			}
		
			/*Student.prototype.setAge =function(age){
				this.age=age;
			    不可以使用原型链寻找到age参数，因为student的原型person里没有age
			}*/
		
			Student.prototype = new Person(name);
			
- 阅读javascript代码，回答问题(输出是什么，为什么？)

		if(! "a" in window){
		    var a = 1;
		}
		alert(a);
		变量提前问题，等价于：
		
		var a;
		if(!"a"in window){
		    a =1;
		}
		alert(a);//undefined

- 阅读javascript代码，回答问题(输出是什么，为什么？)

		var myObject = {
		    foo: "bar",
		    func: function() {
		        var self = this;
		        console.log(this.foo);  
		        console.log(self.foo);  
		        (function() {
		            console.log(this.foo);  
		            console.log(self.foo);  
		        }());
		    }
		};
		myObject.func();
		1.第一个this.foo输出bar，因为当前this指向对象myObject。
		2.第二个self.foo输出bar，因为self是this的副本，同指向myObject对象。
		3.第三个this.foo输出undefined，因为这个IIFE(立即执行函数表达式)中的this指向window。
		4.第四个self.foo输出bar，因为这个匿名函数所处的上下文中没有self，所以通过作用域链向上查找，从包含它的父函数中找到了指向myObject对象的self。
		
- 阅读javascript代码，回答问题(输出是什么，为什么？)

		var Obj=function(msg){
		               this.msg=msg;
		               this.shout=function(){
		                      alert(this.msg);
		               }
		                  this.waitAndShout=function(){                               
		                                setTimeout(this.shout, 2000);
		               }
		        }
		 
		        var aa=new Obj("abc");
		 
		        aa.waitAndShout();
		        输出undefined;
		        1.setTimeout(this.shout, 2000); 改为this.shout(),立即执行shout，
		        没有延迟执行，可以弹出abc，但不符合出题目的
		        2.this.shout=function(){        改为  var that = this;this.shout=function(){
		                      alert(this.msg);					 alert(that.msg);
		               }							}//也没有延迟执行
			3.this.waitAndShout=function(){
			    var _this = this;
			    setTimeout(function(){
			        _this.shout();
			    }, 2000);
			}//使用闭包正确解法。定义私有属性_this指向Obj
			//setTimeout(this.shout, 2000);
			//没有括号是返回函数的引用，当setTimeout定时执行函数时是以普通的函数来执行的，
			//不是以Obj对象的方法来执行，函数中的this===window。
			//setTimeout(this.shout(), 2000);
			//有括号是立即执行this.shout()，和setTimeout没有关系了
			//此时function(){...}没有()，不是立即调用
		
- 购物车的实现原理？
- 加载异步脚本的艺术

Facebook 插件js jdk写法
<script>
(function(d,s,id){
	var js , fjs = d.getElementsByTagName(s)[0];//防止找不到head等标签，必然存在一个script标签
	if(d.getElementById(id)) return; //防止脚本多次引用
	js= d.createElement(s) ; js.id = id;
	js.src = "//connect.facebook.net/en_US/all.ks#xfbml=1";
	fjs.parentNode.insertBefore(js,fjs);

})(document,'script','facebook-jssdk');
</script>		

## <a name='other'>其他问题</a>

- gulp和grunt的比较

		易用 Gulp相比Grunt更简洁，而且遵循代码优于配置策略，维护Gulp更像是写代码。
		
		高效 Gulp相比Grunt更有设计感，核心设计基于Unix流的概念，通过管道连接，不需要写中间文件。
		
		高质量 Gulp的每个插件只完成一个功能，这也是Unix的设计原则之一，各个功能通过流进行整合并完成复杂的任务。例如：Grunt的imagemin插件不仅压缩图片，同时还包括缓存功能。他表示，在Gulp中，缓存是另一个插件，可以被别的插件使用，这样就促进了插件的可重用性。目前官方列出的有673个插件。
		
		易学 Gulp的核心API只有5个，掌握了5个API就学会了Gulp，之后便可以通过管道流组合自己想要的任务。
	[原文](https://segmentfault.com/a/1190000002491282)

- 知道nginx吗？ 干什么用的？

	[知乎介绍](http://www.zhihu.com/question/21483073)

- 输入url到显示页面发生了什么？

		作一个简单粗暴的描述，假设是简单的HTTP请求，IPV4，没有代理。
		1.浏览器查询缓存，如果缓存存在跳到第9步。
		
		2.浏览器询问操作系统服务器的IP地址。
		
		3.操作系统做DNS查询，返回IP地址给浏览器。
		
		4.浏览器打开对服务器的TCP连接（如果是HTTPS协议的话会更复杂）。
		
		5.浏览器通过TCP连接发送HTTP请求。
		
		6.浏览器接收HTTP响应并且可能关掉TCP连接，或者是重新使用连接处理新请求。
		
		7.浏览器检查HTTP响应是否为一个重定向（3xx 结果状态码 ），一个验证请求（401）
		，错误（4xx 5xx）等等，这些都是不同响应的正常处理（2xx）.
		
		8.如果响应可缓存，将存入缓存。
		
		9.浏览器解码响应（例如：如果它是gzziped压缩）。
		
		10.浏览器决定如何处理这些响应（例如，它是HTML页面，一张图片，一段音乐）。
		
		11.浏览器展现响应，对未知类型还会弹出下载对话框。
		
		这里边的每个步骤都可以长篇大论一番，当然还有很多东西与这些步骤平行发生。
		（完）
		
- 浏览器占用内存比较，为什么浏览器占用内存大？

		插件、多媒体等，因为现代浏览器特别是chrome，为浏览器每个动作都单独打开一个进程。

- 各种排序算法的时间空间复杂度

![sort](http://blog.chinaunix.net/attachment/201201/18/21457204_1326898064RUxx.jpg)

- 原来公司工作流程是怎么样的，如何与其他人协作的？如何夸部门合作的？

- 你遇到过比较难的技术问题是？你是如何解决的？

- 设计模式 知道什么是singleton, factory, strategy, decrator么?

- 常使用的库有哪些？常用的前端开发工具？开发过什么应用或组件？

- 页面重构怎么操作？

- 列举IE与其他浏览器不一样的特性？

- 99%的网站都需要被重构是那本书上写的？

- 什么叫优雅降级和渐进增强？

- WEB应用从服务器主动推送Data到客户端有那些方式？

- 对Node的优点和缺点提出了自己的看法？

- 你有用过哪些前端性能优化的方法？

- http状态码有那些？分别代表是什么意思？

- 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？（流程说的越详细越好）

- 除了前端以外还了解什么其它技术么？你最最厉害的技能是什么？

- 你用的得心应手用的熟练地编辑器&开发环境是什么样子？

- 对前端界面工程师这个职位是怎么样理解的？它的前景会怎么样？

- 你怎么看待Web App 、hybrid App、Native App？

- 你移动端前端开发的理解？（和 Web 前端开发的主要区别是什么？）

- 你对加班的看法？

- 平时如何管理你的项目？

- 每个模块的代码结构都应该比较简单，且每个模块之间的关系也应该非常清晰，随着功能和迭代次数越来越多，你会如何去保持这个状态的？

- Git知道branch, diff, merge么?

- 如何设计突发大规模并发架构？

- 当团队人手不足，把功能代码写完已经需要加班的情况下，你会做前端代码的测试吗？

- 说说最近最流行的一些东西吧？平时常去哪些网站？

- 知道什么是SEO并且怎么优化么? 知道各种meta data的含义么?

- 移动端（Android IOS）怎么做好用户体验?

- 你在现在的团队处于什么样的角色，起到了什么明显的作用？

- 你认为怎样才是全端工程师（Full Stack developer）？

- 介绍一个你最得意的作品吧？

- 你有自己的技术博客吗，常去那些博客？

	[GabrielchenCN](http://www.cnblogs.com/gabrielchen/)

- 对前端安全有什么看法？


- 最近在学什么东西吗？

- 能谈谈你未来3，5年给自己的规划吗？
- 解释一下xss 攻击，他的原理和危害

		跨站脚本攻击(Cross Site Scripting)
		主要就是通过上次文本或者访问url是注入js代码（或经过编码的js代码），达到转移访问地址，
		获取session等信息，注入数据库等功能
[例子](http://www.cnblogs.com/bangerlee/archive/2013/04/06/3002142.html)
[XSS防护](http://fex.baidu.com/blog/2014/06/xss-frontend-firewall-1/)

- http 304状态码的原理
		
		客户端是怎么知道这些内容没有更新的呢？其实这并不是客户端的事情，而是你服务器的事情，
		大家都知道服务器可以设置缓存机制，这个功能是为了提高网站的访问速度，
		当你发出一个GET请求的时候服务器会从缓存中调用你要访问的内容，这个时
		候服务器就可以判断这个页面是不是更新过了，如果没有更新过那么他会给你
		返回一个304状态码。
- http常见的响应头、请求头

		用于HTTP请求中的常用请求头字段
		Accept：用于高速服务器，客户机支持的数据类型
		Accept-Charset：用于告诉服务器，客户机采用的编码格式
		Accept-Encoding：用于告诉服务器，客户机支持的数据压缩格式
		Accept-Language：客户机的语言环境
		Host：客户机通过这个头高速服务器，想访问的主机名
		If-Modified-Since：客户机通过这个头告诉服务器，资源的缓存时间
		Referer：客户机通过这个头告诉服务器，它是从哪个资源来访问服务器的（防盗链）
		User-Agent：客户机通过这个头告诉服务器，客户机的软件环境
		Cookie：客户机通过这个头可以向服务器带数据
		Connection：处理完这次请求后是否断开连接还是继续保持连接
		Date：当前时间值
		
		HTTP响应
		状态行：用于描述服务器对请求的处理结果。
		状态码：100~199：表示成功接收请求，要求客户端继续提交下一次请求才能完成整个处理过程。
		 200~299：表示成功接收请求并已完成整个处理过程。常用200
		 300~399：为完成请求，客户需进一步细化请求。例如：请求的资源已经移动一个新地址、常用302（意味着你请求我，我让你去找别人）,307和304（我不给你这个资源，自己拿缓存）
		 400~499：客户端的请求有错误，常用404（意味着你请求的资源在web服务器中没有）403（服务器拒绝访问，权限不够）
		 500~599：服务器端出现错误，常用500
		多个响应头：响应头用于描述服务器的基本信息，以及数据的描述，服务器通过这些数据的描述信息，可以通知客户端如何处理等一会儿它回送的数据。
		Location：这个头配合302状态码使用，用于告诉客户找谁。
		Server：服务器通过这个头告诉浏览器服务器的类型。
		Content-Encoding：服务器通过这个头告诉浏览器数据的压缩格式。
		Content-Length：服务器通过这个头告诉浏览器回送数据的长度
		Content-Type：服务器通过这个头告诉浏览器回送数据的类型
		Last-Modified：告诉浏览器当前资源的最后缓存时间
		Refresh：告诉浏览器隔多久刷新一次
		Content-Disposition：告诉浏览器以下载方式打开数据
		Transfer-Encoding：告诉浏览器数据的传送格式
		ETag：缓存相关的头
		········三种禁止浏览器缓存的头字段：
		 Expires：告诉浏览器把回送的资源缓存多长时间 -1或0则是不缓存
		 Cache-Control：no-cache
		 Pragma：no-cache
		服务器通过以上两个头，也就是控制浏览器不要缓存数据
		实体内容：代表服务器向客户端回送的数据

## <a name='company'>对于公司的问题</a>

- 公司目前产品所应用的技术，和公司未来可能的技术方向。
- 公司的前端团队有多少人，新老员工比重如何，开发流程是怎么样的，如何进行项目进度控制。
- 公司有什么样的培训制度。
- 公司提供VPN或者其他科学上网工具吗？可以在非办公时间使用吗？
- 公司的考核标准是什么样的。
- 公司的作息时间，请假流程。
- 劳动合同签署时间长度

## 有趣的问题


- .A、B两人分别在两座岛上。B生病了，A有B所需要的药。C有一艘小船和一个可以上锁的箱子。C愿意在A和B之间运东西，但东西只能放在箱子里。只要箱子没被上锁，C都会偷走箱子里的东西，不管箱子里有什么。如果A和B各自有一把锁和只能开自己那把锁的钥匙，A应该如何把东西安全递交给B？


	    答案：A把药放进箱子，用自己的锁把箱子锁上。B拿到箱子后，再在箱子上加一把自己的锁。
	    箱子运回A后，A取下自己的锁。箱子再运到B手中时，B取下自己的锁，获得药物。

- Amazon主页的左上角有一个商品分类浏览的下拉菜单 没有延迟，而且子菜单也不会在不应该的时候消失。它是怎样做到这一点的呢？

	 	 答案是通过探测鼠标移动的方向和轨迹，具体查看Khan Academy工程师 Ben Kamens 写的 jQuery插件
![这是 Khan Academy工程师 Ben Kamens 写的 jQuery插件](http://a.36krcnd.com/photo/3f716d75a80cdce23c803fc6f088846e.png)

## 好用的工具，插件
   1.[SublimeCodeIntel](https://github.com/SublimeCodeIntel/SublimeCodeIntel) 
   2.Emmet
   3.jsformat
   4.jade
   5.package control


## <a name='web'>前端学习网站推荐</a>
	
	1. 极客标签：     http://www.gbtags.com/

	2. 码农周刊：     http://weekly.manong.io/issues/
	
	3. 前端周刊：     http://www.feweekly.com/issues
	
	4. 慕课网：       http://www.imooc.com/
	
	5. div.io：		 http://div.io 
	
	6. Hacker News： https://news.ycombinator.com/news
	
	7. InfoQ：       http://www.infoq.com/
	
	8. w3cplus：     http://www.w3cplus.com/
	
	9. Stack Overflow： http://stackoverflow.com/
	
	10.w3school：    http://www.w3school.com.cn/

	11.mozilla：     https://developer.mozilla.org/zh-CN/docs/Web/
	
	12.codepen：   



## <a name='web'>文档推荐</a>

	
1. [jQuery 基本原理](http://docs.huihoo.com/jquery/jquery-fundamentals/zh-cn/index.html "jQuery 基本原理")


2. [JavaScript 秘密花园](http://bonsaiden.github.io/JavaScript-Garden/zh/)


3. [CSS参考手册](http://css.doyoe.com/)



###更新时间:  2016/01/27
