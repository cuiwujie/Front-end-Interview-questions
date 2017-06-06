# 方法定义

## Call方法

语法：语法：call([thisObj[,arg1[, arg2[,   [,.argN]]]]]) 

定义：调用一个对象的一个方法，以另一个对象替换当前对象。

说明： call 方法可以用来代替另一个对象调用一个方法。call 方法可将一个函数的对象上下文从初始的上下文改变为由 thisObj 指定的新对象。 
如果没有提供 thisObj 参数，那么 Global 对象被用作 thisObj。 

## apply方法

语法：apply([thisObj[,argArray]]) 

定义：应用某一对象的一个方法，用另一个对象替换当前对象。 

说明： 如果 argArray 不是一个有效的数组或者不是 arguments 对象，那么将导致一个 TypeError。 
如果没有提供 argArray 和 thisObj 任何一个参数，那么 Global 对象将被用作 thisObj， 并且无法被传递任何参数。


唯一区别是apply接受的是数组参数，call接受的是连续参数。

## 实例

	<script>
    function add(j, k){
        console.log(j+k);
    }

    function sub(j, k){
        console.log(j-k);
    }

    add(5,3); //8
    add.call(sub, 5, 3); //8
    add.apply(sub, [5, 3]); //8

    sub(5, 3); //2
    sub.call(add, 5, 3); //2
    sub.apply(add, [5, 3]); //2

	</script>

## 通过call和apply，我们可以实现对象继承。示例：

	var Parent = function(){
    this.name = "yjc";
    this.age = 22;
	}
	
	var child = {};
	console.log(child);//Object {} ,空对象
	
	Parent.call(child);
	console.log(child); //Object {name: "yjc", age: 22}

## call、apply有什么作用 

我们经常会在我们项目中做一些通用的对象，这些对象用来处理我们的一些通用的过程。

	/*通用验证对象*/
	var validator = {
	    validateName : function(){
	         console.log(this.name);
	    },
	    validateAge  : function(){
	         console.log(this.age)
	    }
	    //.....
	}

	/*对象kobe*/
	var kobe = {
	    name : 'kobe bryant',
	    age  : -1
	}
	
	/*对象 allen*/ 
	var allen = {
	    name : 'allen iverson',
	    age  : 10
	}

	
	var isKobeAgeValid = validator.call(kobe);
	
	var isAllenAgeValid = validator.call(allen);

## 用处与区别


1. call, apply作用就是借用别人的方法来调用,就像调用自己的一样.

2. call, apply方法区别是,从第二个参数起, call方法参数将依次传递给借用的方法作参数, 而apply直接将这些参数放到一个数组中再传递, 最后借用方法的参数列表是一样的。