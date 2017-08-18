# 数据类型

基本数据类型

1. 字符串型（String）

2. 数字型（Number）

3. 布尔型（Boolean）

4. 原始值（Null）

5. 未定义（undefined）

引用数据类型

1. Object类型 
2. Array类型
3. Date类型
4. RegExp类型
5. Function类型 

判断类型
## Typeof操作符

typeof会返回一个变量的基本类型，只有以下几种：number,boolean,string,object,undefined,function；例：

## Instanceof用于检测引用类型

instanceof返回的是一个布尔值

instanceof只能用来判断对象和函数，不能用来判断字符串和数字等

## 准确判断

Object.prototype.toString.call(obj) === "[object Array]"; 

Object.prototype.toString.call(obj) === "[object object]"; 
