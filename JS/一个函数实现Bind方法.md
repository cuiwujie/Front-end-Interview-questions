## Bind

bind() 方法为被选元素添加一个或多个事件处理程序，并规定事件发生时运行的函数。

首先bind不同于call和apply只是单纯地设置this的值后传参，它还会将所有传入bind()方法中的实参（第一个参数之后的参数）与this一起绑定。


 bind()方法所返回的函数的length（形参数量）等于原函数的形参数量减去传入bind()方法中的实参数量（第一个参数以后的所有参数），因为传入bind中的实参都会绑定到原函数的形参。

	function  func(a,b,c,d){...} //func的length为4

	var after = func.bind(null,1,2)  //这里输入了两个实参（1，2）绑定到了func函数的a，b
	
	console.log(after.length) //after的length为 2

第三，当bind()所返回的函数用作构造函数的时候， 传入bind()的this将被忽略，实参会全部传入原函数

	function original(x){
	  this.a=1;
	  this.b =function(){return this.a + x}
	}
	var obj={
	  a:10
	}
	var  newObj = new (original.bind(obj,2)) //传入了一个实参2
	console.log(newObj.a)  //输出 1, 说明返回的函数用作构造函数时obj(this的值)被忽略了
