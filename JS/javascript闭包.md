# javascript 闭包

闭包是指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量，利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。

闭包特性：

(1)函数内再嵌套函数

(2)内部函数可以引用外层的参数和变量

(3)参数和变量不会被垃圾回收机制回收

学习资料

[学习Javascript闭包（Closure）](http://www.ruanyifeng.com/blog/2009/08/learning_javascript_closures.html)


[破解前端面试（80% 应聘者不及格系列）：从闭包说起](https://juejin.im/post/58f1fa6a44d904006cf25d22)

[详解js闭包](http://segmentfault.com/a/1190000000652891)

## 一、变量的作用域

要理解闭包，首先必须理解Javascript特殊的变量作用域，变量的作用域无非就是两种：全局变量和局部变量。Javascript语言的特殊之处，就在于函数内部可以直接读取全局变量。


	var n=999;
	function f1(){
	　　alert(n);
	}; 
	f1(); // 999
　　  


另一方面，在函数外部自然无法读取函数内的局部变量。

	　function f1(){
	　　　　var n=999;
	　}
	　alert(n); // error

这里有一个地方需要注意，函数内部声明变量的时候，一定要使用var命令。如果不用的话，你实际上声明了一个全局变量！

	function f1(){
	　　　　n=999;
	　　}
	f1();
	alert(n); // 999

## 如何从外部读取局部变量
我们有时候需要得到函数内的局部变量。但是，前面已经说过了，正常情况下，这是办不到的，只有通过变通方法才能实现。

	function f1(){
	　　　var n=999;
	　　　function f2(){
	　　　　　　alert(n); // 999
	　　　}
	}

在上面的代码中，函数f2就被包括在函数f1内部，这时f1内部的所有局部变量，对f2都是可见的。但是反过来就不行，f2内部的局部变量，对f1就是不可见的。这就是Javascript语言特有的"链式作用域"结构（chain scope），子对象会一级一级地向上寻找所有父对象的变量。所以，父对象的所有变量，对子对象都是可见的，反之则不成立。

既然f2可以读取f1中的局部变量，那么只要把f2作为返回值，我们不就可以在f1外部读取它的内部变量了吗！

	 function f1(){
	　　　　var n=999;
	　　　　function f2(){
	　　　　　　alert(n); 
	　　　　}
	　　　　return f2;
	　　}
	　　var result=f1();
	　　result(); // 999

## 三、闭包的概念

闭包就是能够读取其他函数内部变量的函数。由于在Javascript语言中，只有函数内部的子函数才能读取局部变量，因此可以把闭包简单理解成"定义在一个函数内部的函数"。所以，在本质上，闭包就是将函数内部和函数外部连接起来的一座桥梁。

## 四、闭包的用途

闭包可以用在许多地方。它的最大用处有两个，一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。

## 五、使用闭包的注意点

1）由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。

2）闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值。

## 实例1
	 var name = "The Window";
    var object = {
        name : "My Object",
        getNameFunc : function(){
            return function(){
                return this.name;
            };
        }
    };
    console.log(object.getNameFunc()());//The Window

	var object1 = {
        name : "My Object",
        getNameFunc : function(){
            var that = this;
            return function(){
                return that.name;
            };
        }
    };
    console.log(object1.getNameFunc()());//My Object



	
