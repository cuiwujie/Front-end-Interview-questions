# 创建对象的方式

javascript创建对象简单的说,无非就是使用内置对象或各种自定义对象，当然还可以用JSON；但写法有很多种，也能混合使用。

# 对象字面量的方式
person={firstname:"Mark",lastname:"Yun",age:25,eyecolor:"black"};
# 用function来模拟无参的构造函数

	function Person(){}
	var person = new Person(); //定义一个function，如果使用new"实例化",该function可以看作是一个Class
	person.name = "Xiaosong";
	person.age = "23";
	person.work = function() {
	  alert("Hello " + person.name);
	}
	person.work();

# 用function来模拟参构造函数来实现（用this关键字定义构造的上下文属性）

	function Person(name,age,hobby) {
	  this.name = name; //this作用域：当前对象
	  this.age = age;
	  this.work = work;
	  this.info = function() {
	      alert("我叫" + this.name + "，今年" + this.age + "岁，是个" + this.work);
	  }
	}
	var Xiaosong = new Person("WooKong",23,"程序猿"); //实例化、创建对象
	Xiaosong.info(); //调用info()方法

# 用工厂方式来创建（内置对象）

	var jsCreater = new Object();
	jsCreater.name = "Brendan Eich"; //JavaScript的发明者
	jsCreater.work = "JavaScript";
	jsCreater.info = function() {
	  alert("我是"+this.work+"的发明者"+this.name);
	}
	jsCreater.info();

# 用原型方式来创建

	function Standard(){}
	Standard.prototype.name = "ECMAScript";
	Standard.prototype.event = function() {
	  alert(this.name+"是脚本语言标准规范");
	}
	var jiaoben = new Standard();
	jiaoben.event();

# 用混合方式来创建

	function iPhone(name,event) {
	  this.name = name;
	  this.event = event;
	}
	iPhone.prototype.sell = function() {
	  alert("我是"+this.name+"，我是iPhone5s的"+this.event+"~ haha!");
	}
	var SE = new iPhone("iPhone SE","官方翻新机");
	SE.sell();

# new 操作符

(1)创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。

(2)属性和方法被加入到 this 引用的对象中。

(3)新创建的对象由 this 所引用，并且最后隐式的返回 this 。

		var arr = new Array;


		var arr={};
		arr.__proto__=Array.prototype
