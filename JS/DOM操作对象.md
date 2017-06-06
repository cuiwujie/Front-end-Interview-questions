
![](http://files.jb51.net/file_images/article/201412/201412111054092.png)
# 节点的分类  

1. 元素节点：html中的标签都是元素节点、如<a>、<body>......

2. 文本节点：向用户展示的内容，如<li>xxx</li>、<a href="#">xxx</a>里的xxx内容文本

3. 属性节点：元素的属性、如<a>标签里的链接属性

# 节点的属性

1、节点的名称：nodeName

元素节点的名称和标签名相同、文本节点的名称永远是#text、属性节点的名称是属性名、文档节点永远是#document。

2、节点的值：nodeValue

元素节点的值是undefined或null、文本节点的值是文本内容、属性节点的值是属性本身。

3、节点的类型：nodeType

	元素类型	节点类型
	元素			1
	属性			2
	文本			3
	注释			8
	文档			9
# 节点操作

1. getElementByName()方法

  document.getElementByName(name)

2. getElementsByTagName()方法
 
 document.getElementsByTagName(TagName)
	
		<html>  
		 <head>
         <script>
         function test() {
         testall=document.getElementsByTagName("body");
         testbody=testall.item(0); //获得所有tagName是body的元素（当然每个页面只有一个）
         testall=testbody.getElementsByTagName("p");// 获得body子元素种的所有P元素
         testnode=testall.item(1); // 获得第二个P元素         alert(testnode.firstChild.nodeValue); //显示这个元素的文本         }
         </script>
         </head>
         <body>
         <p>hi</p>
         <p>hello</p>
         <script language="javascript">
         test();
         </script>
         </body>
         </html>

3. getElementById()方法

document.getElementById(id)

 		<body>
         <div id="myid">
         	test
         </div>
         <script language="javascript">
         	alert(document.getElementById("myid").innerHTML);
         </script>
         </body>

4. getAttribute()方法

> 创建节点

createElement()

> 创建文本节点

createTextNode()

> 插入节点到最后

appendChild()


		<html>
         
         <head>
         </head>
		<body>
         <div id="test"></div>
         <script type="text/javascript">
         var newdiv=document.createElement("div")
         var newtext=document.createTextNode("A new div")         newdiv.appendChild(newtext)
         document.getElementById("test").appendChild(newdiv)
         </script>
         </body>
         </html>
> 插入节点到目标节点的前面

insertBefore()

> 复制节点

node.cloneNode(true);
node.cloneNode(false);

		<html>
		<head>
         </head>
         <body>
         <p id="mynode">test</p>
         <script language="javascript">
         p=document.getElementById("mynode")
        pclone = p.cloneNode(true);
         p.parentNode.appendChild(pclone);
         </script>
         </body>
         </html>

复制上面的div节点，参数true，复制整个节点和里面的内容；false，只复制节点不要里面的内容，复制后的新节点，也不会被自动插入到文档

> 删除节点

removeChild()

		<html>
 		<head>
         </head>
         <body>
         <div id="parent"><div id="child">A child</div></div>
         <script language="javascript">
         var childnode=document.getElementById("child")
         var removednode=document.getElementById("parent").removeChild(childnode)
         </script>
         </body>
         </html>

> 替换节点

repalceChild(newNode, oldNode)

		<html>
		<head>
         </head>
         <body>
         <div id="mynode2">
         <span id="orispan">span</span>
         </div>
         <script language="javascript">
         var orinode=document.getElementById("orispan");
         var newnode=document.createElement("p");
         var text=document.createTextNode("test ppp ");
         newnode.appendChild(text);
         document.getElementById("mynode2").replaceChild(newnode, orinode);
         </script>
         </body>
</html>

> 设置节点属性

setAttribute()

> 获取节点属性

getAttribute()

> 判断元素是否有子节点

hasChildNodes

1、firstElementChild        第一个子元素节点
2、lastElementChild        最后一个子元素节点
3、nextElementSibling        下一个兄弟元素节点
4、previousElementSibling    前一个兄弟元素节点
5、childElementCount        子元素节点个数量