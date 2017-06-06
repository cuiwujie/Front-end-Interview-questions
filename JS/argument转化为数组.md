# 将arguments转化为Array的方式
1. slice
	function slice() {
	  return Array.prototype.slice.call(arguments);
	}

2. ArrayPush

	function forAndArrayPush() {
	  var args = [];
	  for (var i = 0, l = arguments.length; i < l; i++) {
	    args.push(arguments[i]);
	  }
	  return args;
	}

3. ArraySet

	function forAndArraySet() {
	  var args = [];
	  for (var i = 0, l = arguments.length; i < l; i++) {
	    args[i] = arguments[i];
	  }
	  return args;
	}
4. Array.prototype.slice.call
Array.prototype.slice.call(arguments)能将具有length属性的对象转成数组
	
	Array.prototype.slice.call(arguments)