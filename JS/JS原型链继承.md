[详解继承1！](https://segmentfault.com/a/1190000008739672)
[详解继承2！](https://segmentfault.com/a/1190000008754962)
1.每个对象都会在其内部初始化一个属性，就是prototype(原型)，当我们访问一个对象的属性时，如果这个对象内部不存在这个属性，那么他就会去prototype里找这个属性，这个prototype又会有自己的prototype，
于是就这样一直找下去，也就是我们平时所说的原型链的概念。
关系：instance.constructor.prototype = instance.__proto__
//
1. 特点：JavaScript对象是通过引用来传递的，我们创建的每个新对象实体中并没有一份属于自己的原型副本，当我们修改原型时，与之相关的对象也会继承这一改变。
//
1. 当我们需要一个属性时，JavaScript引擎会先看当前对象中是否有这个属性，如果没有的话，就会查找它的prototype对象是否有这个属性，如此递推下去，一致检索到Object内建对象。

		function Func(){}
		Func.prototype.name = "Xiaosong";
		Func.prototype.getInfo = function() {
		  return this.name;
		}
		var person = new Func();
		console.log(person.getInfo());
		//"Xiaosong"
		console.log(Func.prototype);
		//Func { name = "Xiaosong", getInfo = function() }

