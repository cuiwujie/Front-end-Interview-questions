---
title: THe_font-Size
date: 2017-04-14 16:58:23
tags: font-Size
---
# web端的字体单位大小设置


## PX为单位

在Web页面初期制作中，我们都是使用“px”来设置我们的文本，因为他比较稳定和精确。但是这种方法存在一个问题，当用户在浏览器中浏览我们制作的Web页面时，他改变了浏览器的字体大小，这时会使用我们的Web页面布局被打破。这样对于那些关心自己网站可用性的用户来说，就是一个大问题了。因此，这时就提出了使用“em”来定义Web页面的字体。

## em为单位

一般都是以<body>的“font-size”为基准。比如说我们使用“1em”等于“10px”来改变默认值“1em=16px”，这样一来，我们设置字体大小相当于“14px”时，只需要将其值设置为“1.4em”。

	body {
		font-size: 62.5%;/*10 ÷ 16 × 100% = 62.5%*/
	}
	h1 {
		font-size: 2.4em; /*2.4em × 10 = 24px */
	}
	p	{
		font-size: 1.4em; /*1.4em × 10 = 14px */
	}
	li {
		font-size: 1.4em; /*1.4 × ? = 14px ? */
	}

在使用“em”作单位时，一定需要知道其父元素的设置，因为“em”就是一个相对值，而且是一个相对于父元素的值，其真正的计算公式是：

	1 ÷ 父元素的font-size × 需要转换的像素值 = em

## Rem为单位

W3C官网上描述:"font size of the root element" 

“em”是相对于其父元素来设置字体大小的，这样就会存在一个问题，进行任何元素设置，都要知道它父元素的大小。所以在使用的时候就会出现不可预知的问题。

"Rem"是相对于<html>的，这样就意味着只需要在根元素下设置一个参考值就OK了。参考如下图：

![](http://onnq25vz1.bkt.clouddn.com/emTable.png)

案例：
	
			html {font-size: 62.5%;/*10 ÷ 16 × 100% = 62.5%*/}
			body {font-size: 1.4rem;/*1.4 × 10px = 14px */}
			h1 { font-size: 2.4rem;/*2.4 × 10px = 24px*/}

## 浏览器的兼容性


rem是CSS3新引进来的一个度量单位，支持的浏览器：Mozilla Firefox 3.6+、Apple Safari 5+、Google Chrome、IE9+和Opera11+。只是IE6-8无法支持，如果想兼容IE下的效果，可你可考虑“px”和“rem”一起使用，用"px"来实现IE6-8下的效果，然后使用“Rem”来实现代浏览器的效果

## rem知识点

rem（font size of the root element）是指相对于根元素的字体大小的单位。简单的说它就是一个相对单位。看到rem大家一定会想起em单位，em（font size of the element）是指相对于父元素的字体大小的单位。它们之间其实很相似，只不过一个计算的规则是依赖根元素一个是依赖父元素计算。

[http://isux.tencent.com/web-app-rem.html?utm_source=caibaojian.com](http://isux.tencent.com/web-app-rem.html?utm_source=caibaojian.com "web app变革之rem")

[http://caibaojian.com/web-app-rem.html](http://caibaojian.com/web-app-rem.html)

