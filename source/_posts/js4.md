---
title: js第四天
tags: [笔记,随笔,美文]
categories: 笔记
---




# 对象

> 习目标：1. 会创建一个对象  2. 会定义一个构造函数  3. 会操作一个对象

## 对象的基本概念

### 为什么要有对象？

> 现实生活中：因为我们没有对象，所以我们要学习对象了，有了对象的好处友哪些?
>
> 在javascript中：对象跟数组、函数一样，都是一种复杂数据类型，是一系列相关的属性的集合，可以很方便对变量和函数进行管理。

<font color="red">学习对象，大家会痛并快乐着，痛是因为第一次接触对象，对象操作的语法会很不习惯。快乐是 因为学习完对象，YY又提升到了一个新高度。</font>



### 什么是对象？

> 现实生活中：万物皆对象，对象是一个具体的事物，一个具体的事物就会有行为和特征。
>
> javascript中：javascript中的对象其实就是生活中对象的一个抽象。

+ 事物的特征在对象中用属性来表示。
+ 事物的行为在对象中用方法来表示。

思考：

```javascript
1. 女友对象
	//特征：名字、性别、身高、体重、血型、星座、生日
	//行为：吃饭、睡觉、拍电影、唱歌、发微博
2. 学生对象
	//特征：名字、性别、身高、体重、分数
	//行为：吃饭、睡觉、学习、敲代码
3. 英雄对象
	//特征：名字、性别、金钱、等级、技能
	//行为：移动、攻击、防御
```



## 创建对象

### 通过构造函数创建

```javascript
var hero = new Object();//创建一个空的对象

hero.name = "德玛";//给对象添加一个属性  .代表的
hero.skill = "争议审判";

hero.attack = function() {
  console.log("德玛攻击了小怪物");
}
```



1. this一定要出现在方法中才有意义，不在方法中的this没有意义。
2. 在方法中出现的this，指的是当前对象，即调用这个方法的对象



### 对象字面量

> 字面量：11 “abc”  true  [] {}等

```javascript
var o = {
  name : "zs",
  age : 18,
  sex : true,
  sayHi : function() {
    console.log(this.name);
  }
};

```



思考：

```javascript
如何把学生对象、老师对象、英雄对象改写成字面量的方式
```



## 批量创建对象

### 使用普通函数创建对象

优点：可以同时创建多个对象

缺点：创建出来的没有具体的类型，都是object类型的



### 查看一个对象的类型

```javascript
typeof 只能判断基本数据类型的类型
instanceof 判断对象的具体类型
constructor.name也可以获取到对象的具体类型
```



### 构造函数

> 构造函数 ，是一种特殊的函数。主要用来在创建对象时初始化对象， 即为对象成员变量赋初始值，总与new运算符一起使用在创建对象的语句中。

1. 构造函数用于创建一类对象，首字母要大写。
2. 构造函数要和new一起使用才有意义。

new在执行时会做四件事情

```javascript
    //new会做4件事情
    //1. new会创建一个新的空对象，类型是Teacher
    //2. new 会让this指向这个新的对象
    //3. 执行构造函数  目的：给这个新对象加属性和方法
    //4. new会返回这个新对象
```



思考：

``` javascript
1. 学生对象的构造函数
2. 老师对象的构造函数
3. 英雄对象的构造函数
```



## 操作对象的属性

### .语法

```javascript
// 获取对象属性的语法：
	// 对象.属性：对象的属性
    // 1. 如果有这个属性，直接返回属性值
    // 2. 如果没有这个属性，返回undefined

// 设置对象的属性的语法
    // 对象.属性 = 值
    // 1. 如果对象有这个属性，修改这个属性
    // 2. 如果对象没有这个属性，添加这个属性

```



### []语法

也叫关联数组的方式，其实说白了就是把对象当成数组看待。

```javascript
//获取对象属性
	// 对象['下标']   ：把对象的属性当成下标
//设置对象的属性
	// 对象['下标'] = "值";
```



二者的区别：当属性名是一个字符串存储在变量中的时候，只能使用关联数组的方式。



### 遍历对象

> 通过for..in语法可以遍历一个对象

```
var obj = {};
for (var i = 0; i < 10; i++) {
		obj[i] = i * 2;
}
for(var key in obj) {
		console.log(key + "==" + obj[key]);
}
```



## 值类型与引用类型

>值类型：简单数据类型，基本数据类型，在存储时，变量中存储的是值本身，因此叫做值类型。
>
>引用类型：复杂数据类型，在存储是，变量中存储的仅仅是地址（引用），因此叫做引用数据类型。



思考：

```javascript
//1. 
var num1 = 10;
var num2 = num1;
num1 = 20;
console.log(num1);
console.log(num2);

//2. 
var num = 50;

function f1(num) {
    num = 60;
    console.log(num);
}
f1(num);
console.log(num);

//3. 
var num1 = 55;
var num2 = 66;
function f1(num, num1) {
  num = 100;
  num1 = 100;
  num2 = 100;
  console.log(num);
  console.log(num1);
  console.log(num2);
}

f1(num1, num2);
console.log(num1);
console.log(num2);
console.log(num);
```



思考2：

```javascript
//1. 
function Person(name, age) {
    this.name = name;
    this.age = age;
}
var p1 = new Person("zs", 18);
var p2 = p1;
p2.name = "ls";
console.log(p1.name);
console.log(p2.name);

//2. 
function Person(name, age) {
  this.name = name;
  this.age = age;
}
function f1(p) {
  p.name = "ls";
  console.log(p.name);
}
var p1 = new Person("zs", 18);
console.log(p1.name);
f1(p1);
console.log(p1.name);
```



思考3：

```javascript

    //1. 
    function f1(a, b) {
        a = a + 1;
        b = b + 1;
        console.log("a = " + a);
        console.log("b = " + b);
    }
    var x = 5;
    var y = 6;
    f1(x, y);
    console.log("x = " + x);
    console.log("y = " + y);

	//2. 
    function Person(name, age) {
        this.name = name;
        this.age = age;
    }
    function f2(p) {
        p = new Person("ls", 50);
        p.name = "ww";
        console.log(p.name);
    }
    var p2 = new Person("zs", 18);
    f2(p2);
    console.log(p2.name);


	//3. 
	function f3(arr) {
        arr[0] = 100;
    }
    var array = [1, 2, 3];
    f3(array);
    console.log(array);

	//4. 思考：之前我们自己封装的 function sort(arr){ return arr } 是不是不返回arr也可以？
  
```

