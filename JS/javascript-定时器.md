# 定时器

参考资料

重点查看
[https://juejin.im/post/58f1fa6a44d904006cf25d22](https://juejin.im/post/58f1fa6a44d904006cf25d22)

## setTimeout()

在指定的延迟时间之后调用一个函数或执行一个代码片段。

### 语法

setTimeout这个内置函数的功能是启动一个定时器，这个定时器在指定的延迟时间 (delay，单位为毫秒(ms))过后，将调用指定的回调函数(fn)，函数调用结束后会返回一个唯一的id,需要时可以把这个id专递给clearTimeout(id)内置函数，以便取消定时器，这个内置函数只执行一次。

	var timeoutID = window.setTimeout(code, delay);]

IE0+ 还支持回调参数的传入：
	
	var timeoutID = window.setTimeout(func, delay, [param1, param2, ...]);

## setInterval()

周期性地调用一个函数(function)或者执行一段代码。

### 语法

与setTimeout一样，就不在赘述

由于javascript 的事件循环机制，导致第二个参数并不代表延迟delay毫秒之后立即执行回调函数，而是尝试将回调函数加入到事件队列。实际上，setTimeout 和 setInterval 在这一点上处理又存在区别：

1. setTimeout：延时delay毫秒之后，啥也不管，直接将回调函数加入事件队列。
2. setInterval: 延时delay毫秒之后，先看看事件队列中是否存在还没有执行的回调函数（setInterval的回调函数），如果存在，就不要再往事件队列里加入回调函数了。

![](http://files.jb51.net/file_images/article/201612/20161203230254.png)

![](http://files.jb51.net/file_images/article/201612/20161203230255.png)


Javascript是单线程执行的，也就是无法同时执行多段代码，当某一段代码正在执行的时候，所有后续的任务都必须等待，形成一个队列，一旦当前任务执行完毕，再从队列中取下一个任务。这也常被称为“阻塞式执行”。

	<script>
		 var num = 10;
		 alert(1);
		 num = 20;
		 setTimeout("alert(num)",0);
		 alert(3);17 
	</script>

结果

	1 3 20
