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

		 HTML5 不基于 SGML，因此不需要对DTD进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；
		
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

		 * IE浏览器的内核Trident、Mozilla的Gecko、Chrome的Blink（WebKit的分支）、Opera内核原为Presto，现为Blink;
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

- 请描述一下 cookies，sessionStorage 和 localStorage 的区别？

- iframe有那些缺点？

- Label的作用是什么？是怎么用的？（加 for）

- HTML5的form如何关闭自动完成功能？给不想要提示的input是设置autocomplete=off即可

- 如何实现浏览器内多个标签页之间的通信? (阿里)

- 如何使用websocket？如何兼容低浏览器？(阿里)

- 页面可见性（Page Visibility）API 可以有哪些用途？

## <a name='css'>CSS</a>

- CSS选择符有哪些？哪些属性可以继承？
 
- CSS优先级算法如何计算？ 

- CSS3新增伪类有那些？

- CSS3有哪些新特性（包含哪些模块）？

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
[CSS奇淫巧计]('http://www.cnblogs.com/2050/p/3392803.html')

- 介绍一下标准的CSS的盒子模型？与低版本IE的盒子模型有什么不同的？

		标准CSS盒子模型有：border content padding margin ,其中width，height是content大小
		ie盒子模型有： border content padding margin ,其中width,height是content+border+padding大小

- display有哪些值？说明他们的作用。position的值relative和absolute定位原点是？

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
		

## <a name='js'>JavaScript</a>

-  用原生JavaScript的实现过什么功能吗？

-  JavaScript 实现数组去重   

-  介绍JavaScript的基本数据类型。

-  说说写JavaScript的基本规范？

-  请解释一下JavaScript原型(prototype)? 每个JS对象都有原型属性吗？

-  JavaScript有几种类型值？（堆：原始值和 栈：引用值），你能画一下他们的内存图吗？

-  Javascript如何实现继承？
  
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

-  什么是window对象? 什么是document对象?

-  null，undefined的区别？

-  用过typeOf 和 instanceOf吗？ 说说他们的区别


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
		

-  写一个通用的事件侦听器函数(机试题)。

-  ["1", "2", "3"].map(parseInt) 答案是多少？

		[1,NaN,NaN]
		因为 parseInt 需要两个参数 (val, radix)，其中 radix 表示解析时用的基数。map 传了 3 个 (element, index, array)，对应的 radix 不合法导致解析失败
		
	[解析](http://blog.csdn.net/freshlover/article/details/19034079 "解析")


-  关于事件，IE与火狐的事件机制有什么区别？ 如何阻止冒泡？

-  什么是闭包（closure），为什么要用它？

-  "use strict";是什么意思 ? 使用它的有什么好处或坏处？

-  如何判断一个对象是否属于某个类？

-  new操作符具体干了什么呢?

-  Javascript中，有一个函数，执行时对象查找时，永远不会去查找原型，这个函数是？

-  对JSON的了解？

-  `[].forEach.call($$("*"),function(a){
  a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16)
})` 能解释一下这段代码的意思吗？

-  js延迟加载的方式有哪些？

-  ajax是什么，解释一下它的工作原理?

-  同步和异步的区别?

-  如何解决跨域问题?

-  URIError: URI malformed 是什么原因？
		URL格式错误，一般是由于编码错误或编码格式不一致导致
		JavaScript有三个编码函数和三个解码函数，它们应该一一对应
		escape,encodeURI,encodeURIComponent，相应3个解码函数：unescape,decodeURI,decodeURIComponent
		1.encodeURI() 函数可把字符串作为 URI 进行编码。该方法不会对 ASCII 字母和数字进行编码，
		也不会对这些 ASCII 标点符号进行编码： - _ . ! ~ * ' ( ) 。

2.escape:该方法不会对 ASCII 字母和数字进行编码，也不会对下面这些 ASCII 标点符号进行编码： * @ - _ + . / 。其他所有的字符都会被转义序列替换。

3.如果 URI 组件中含有分隔符，比如 ? 和 #，则应当使用 encodeURIComponent() 方法分别对各组件进行编码。


-  JS模块化开发怎么做？

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

-  JavaScript中的作用域与变量声明提升？

-  如何编写高性能的Javascript？

-  那些操作会造成内存泄漏？

-  JQuery的源码看过吗？能不能简单概况一下它的实现原理？

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

- 前端templating(Mustache, underscore, handlebars)是干嘛的, 怎么用?

- 简述一下 Handlebars 的基本用法？

- 简述一下 Handlerbars 的对模板的基本处理流程， 如何编译的？如何缓存的？

- 阅读javascript代码，回答问题(是否通过f取到a和b，如果可以那怎么获取，如果不可以请说出原因)
 
		var F = function(){};
		Object.prototype.a = function(){};
		Function.prototype.b = function(){};
		var f = new F();

- 阅读javascript代码，回答问题(输出是什么，为什么？)

		var a = {n: 1}                 
		var b = a;
		a.x = a = {n: 2}
		console.log(a.x);
		console.log(b.x);
		
		
		//自己都说不通了。。
		第一、二行表示a\b 同时指向{n:1}
		第三行 表达式解析为  a.x = (a = {n: 2})
		执行顺序是左到右，所以有
		a.x=Expression 时，a={n:1} ---->{n:1}.x=Expression，此处是{n:1}内存块被赋值了x
		执行a = {n: 2}时，a被指向到 {n: 2}，此时b=a，也被指向{n:2};
		console.log(a.x);时 a={n: 2} 不是{n:1} 所以没有.x属性 ,a.x 未定义
		console.log(b.x);时 a={n: 2}

		解释
		var a,b,c,d;  
		a=b=c=d={a:1};  
		a.x=a=b.y=b=c.z=c={}  
		console.log(a,b,c,d) 
[详解见评论](http://www.iteye.com/topic/785445 "详解见评论")

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
		
		
- 购物车的实现原理？
		

## <a name='other'>其他问题</a>

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

- 对前端安全有什么看法？

- 最近在学什么东西吗？

- 能谈谈你未来3，5年给自己的规划吗？
- 解释一下xss 攻击，他的原理和危害

		跨站脚本攻击(Cross Site Scripting)
		主要就是通过上次文本或者访问url是注入js代码（或经过编码的js代码），达到转移访问地址，
		获取session等信息，注入数据库等功能
[例子]("http://www.cnblogs.com/bangerlee/archive/2013/04/06/3002142.html")

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

## 有趣的问题


- .A、B两人分别在两座岛上。B生病了，A有B所需要的药。C有一艘小船和一个可以上锁的箱子。C愿意在A和B之间运东西，但东西只能放在箱子里。只要箱子没被上锁，C都会偷走箱子里的东西，不管箱子里有什么。如果A和B各自有一把锁和只能开自己那把锁的钥匙，A应该如何把东西安全递交给B？


	    答案：A把药放进箱子，用自己的锁把箱子锁上。B拿到箱子后，再在箱子上加一把自己的锁。
	    箱子运回A后，A取下自己的锁。箱子再运到B手中时，B取下自己的锁，获得药物。

- Amazon主页的左上角有一个商品分类浏览的下拉菜单 没有延迟，而且子菜单也不会在不应该的时候消失。它是怎样做到这一点的呢？

	 	 答案是通过探测鼠标移动的方向和轨迹，具体查看Khan Academy工程师 Ben Kamens 写的 jQuery插件
![这是 Khan Academy工程师 Ben Kamens 写的 jQuery插件](http://a.36krcnd.com/photo/3f716d75a80cdce23c803fc6f088846e.png)

## 好用的工具，插件
   1.[SublimeCodeIntel](https://github.com/SublimeCodeIntel/SublimeCodeIntel) 


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



## <a name='web'>文档推荐</a>

	
1. [jQuery 基本原理](http://docs.huihoo.com/jquery/jquery-fundamentals/zh-cn/index.html "jQuery 基本原理")


2. [JavaScript 秘密花园](http://bonsaiden.github.io/JavaScript-Garden/zh/)


3. [CSS参考手册](http://css.doyoe.com/)



###更新时间:  2015/9/14
