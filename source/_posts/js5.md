
---
title: js第五天
tags: [笔记,随笔,美文]
categories: 笔记
---

<!-- 中英文符号造成错误 -->




# 内置对象


> JS内置对象就是指Javascript自带的一些对象，供开发者使用，这些对象提供了一些常用的的功能。
>
> 常见的内置对象有Math、String、Array、Date等

内置对象有很多，我们主要是记下这些内置对象的用法即可。但是同学们也不可能一下子记住这么多的方法，因此当同学们忘了某个方法该如何使用的时候，可以通过以下方式查看。

+ 跳转到定义`ctrl+左键`
+ [火狐开发者网站MDN](https://developer.mozilla.org/zh-CN/)
+ [W3School网站](http://www.w3school.com.cn/jsref/)
+ 离线文档
+ 笔记




## Math对象

> Math对象中封装很多与数学相关的属性和方法。

+ 属性PI

  `Math.PI`

+ 最大值/最小值

  ```
  Math.max();
  Math.min();
  ```

+ 取整（★）

  ```javascript
  Math.ceil();//天花板，向上取整
  Math.floor();//地板，向下取整
  Math.round();//四舍五入，如果是.5，则取更大的那个数
  ```

+ 随机数（★）

  ```javascript
  Math.random();//返回一个[0,1)之间的数，能取到0，取不到1
  ```

+ 绝对值

  ```javascript
  Math.abs();//求绝对值
  ```

+ 次幂和平方

  ```javascript
  Math.pow(num, power);//求num的power次方
  Math.sqrt(num);//对num开平方
  ```



## Date对象

> Date对象用来处理日期和时间



+ 创建一个日期对象

  ```javascript
  var date = new Date();//使用构造函数创建一个当前时间的对象
  var date = new Date("2017-03-22");//创建一个指定时间的日期对象
  var date = new Date("2017-03-22 00:52:34");//创建一个指定时间的日期对象
  ```

+ 日期格式化(了解)

  ```javascript
  date.toString();//默认的日期格式
  date.toLocalString();//本地风格的日期格式（兼容性）
  date.toDateString();
  date.toLocalDateString();
  date.toTimeString();
  date.toLocalTimeString();
  ```

+ 获取日期的指定部分

  ```javascript
  getMilliseconds();//获取毫秒值
  getSeconds();//获取秒
  getMinutes();//获取分钟
  getHours();//获取小时
  getDay();//获取星期，0-6    0：星期天
  getDate();//获取日，即当月的第几天
  getMonth();//返回月份，注意从0开始计算，这个地方坑爹，0-11
  getFullYear();//返回4位的年份  如 2016

  //思考：
  //封装一个函数，返回当前的时间，格式是：yyyy-MM-dd HH:mm:ss
  ```

+ 时间戳

  ```javascript
  var date = +new Date();//1970年01月01日00时00分00秒起至现在的总毫秒数

  //思考
  //如何统计一段代码的执行时间？
  ```



## Array对象

> 数组对象在javascript中非常的常用

+ 数组转换（★）

  ```javascript
  //语法：array.join(separator)
  //作用：将数组的值拼接成字符串

  var arr = [1,2,3,4,5];
  arr.join();//不传参数，默认按【,】进行拼接
  arr.join("-");//按【-】进行拼接
  ```

+ 数组的增删操作（★）

  ```javascript
  array.push();//从后面添加元素，返回新数组的length
  array.pop();//从数组的后面删除元素，返回删除的那个元素
  array.unshift();//从数组的前面的添加元素，返回新数组的长度
  array.shift();//从数组的最前面删除元素，返回删除的那个元素

  //练习1
  var arr = ["刘备"];
  //添加数据后变成：["赵云","马超","刘备","关羽","张飞"]
  //删除数据后变成：["关羽","张飞"]

  //练习2
  var arr = ["赵云","马超","刘备","关羽","张飞"];
  //把数组的最后一个元素变成数组的第一个元素
  //把数组的第一个元素变成数组的最后一个元素
  ```

+ 数组的翻转与排序

  ```javascript
  array.reverse();//翻转数组
  array.sort();//数组的排序，默认按照字母顺序排序

  //sort方法可以传递一个函数作为参数，这个参数用来控制数组如何进行排序
  arr.sort(function(a, b){
    //如果返回值>0,则交换位置
    return a - b;
  });
  ```


```javascript
//思考：

//将[3, 6, 1, 5, 10, 2,11]从小到大排列

//将字符串数组按照字符长度从小到大排列

//将学生数组按照年龄从小到大排列
```

+ 数组的拼接与截取

```javascript
  //concat：数组合并，不会影响原来的数组，会返回一个新数组。
  var newArray = array.concat(array2);

  //slice:数组切分，复制数组的一部分到一个新数组，并返回这个数组
  //原来的数组不受影响，包含begin，不包含end
  var newArray = array.slice(begin, end);

  //splice:数组拼接，以新元素来替换旧元素，以此来修改数组的内容，常用语删除数组的某些项
  //start:开始位置  deleteCount:删除的个数  items:替换的内容
  array.slice(start, deleteCount, [items]);



  //练习：
  var arr = [4, 6, 7, 8, 3, 46, 8];
  //从数组中截取一个新的数组[6,7,8,3],返回新的数组
  //删除[6,7,8,3]和替换成[1,1,1]
```

+ 数组查找元素

  ```javascript
  //indexOf方法用来查找数组中某个元素第一次出现的位置，如果找不到，返回-1
  array.indexOf(search, [fromIndex]);

  //astIndexOf()从后面开始查找数组中元素出现位置,如果找不到，返回-1
  array.lastIndexOf(search, [fromIndex]);
  ```

+ 清空数组

  ```javascript
  //1．	array.splice(0,array.leng);//删除数组中所有的元素
  //2．	array.length = 0;//直接修改数组的长度
  //3．	array = [];//将数组赋值为一个空数组，推荐
  ```

+ 数组综合练习

  ```javascript
  var arr = ["c", "a", "z", "a", "x", "a", "a", "z", "c", "x", "a", "x"]
  //1. 找到数组中第一个a出现的位置
  //2. 找到数组中最后一个a出现的位置
  //3. 找到数组中每一个a出现的位置
  //4. 数组去重，返回一个新数组
  //5. 获取数组中每个元素出现的次数
  ```



## String对象

> 字符串可以看成是一个字符数组（伪数组）。因此字符串也有长度，也可以进行遍历。String对象很多方法的名字和和Array的一样。可以少记很多的单词。



+ 查找指定字符串

  ```javascript
  //indexOf:获取某个字符串第一次出现的位置，如果没有，返回-1
  //lastIndexOf:从后面开始查找第一次出现的位置。如果没有，返回-1
  ```

+ 去除空白

  ```javascript
  trim();//去除字符串两边的空格，内部空格不会去除
  ```

+ 大小写转换


```javascript
  //toUpperCase：全部转换成大写字母
  //toLowerCase：全部转换成小写字母
```

+ 字符串拼接与截取

  ```javascript
  //字符串拼接
  //可以用concat，用法与数组一样，但是字符串拼串我们一般都用+

  //字符串截取的方法有很多，记得越多，越混乱，因此就记好用的就行
  //slice ：从start开始，end结束，并且取不到end。
  //substring ：从start开始，end结束，并且取不到end
  // substr ： ：从start开始，截取length个字符。(推荐)
  ```

+ 字符串切割

  ```javascript
  //split:将字符串分割成数组（很常用）
  //功能和数组的join正好相反。
  var str = "张三,李四,王五";
  var arr = str.split(",");
  ```

+ 字符串替换

  ```javascript
  replace(searchValue, replaceValue)
  //参数：searchValue:需要替换的值    replaceValue:用来替换的值
  ```

+ 练习

  ```javascript
  //1. 截取字符串"我爱中华人民共和国"，中的"中华"
  //2. "abcoefoxyozzopp"查找字符串中所有o出现的位置
  //3. 把字符串中所有的o替换成!
  //4. 把一个字符串中所有的空格全部去掉
  //5. 统计一个字符串中每个字符出现的次数
  ```

## 面试题

```javascript
//1. 将字符串 "abcdefg"  翻转成   "gfedcba"
//2. 有一个链接： http://www.baidu.com?name=cc&id=100&desc=很帅 将链接的参数部分转换成一个对象,即{name:"cc", id=100 , desc: "很帅"}
//3. 有一个对象{name:"cc", id:100 , desc: "很帅"}和一个链接http://www.baidu.com,拼接成链接http://www.baidu.com?name=cc&id=100&desc=很帅
```



## 基本包装类型

> **简单数据类型是没有方法的**。为了方便操作基本数据类型，JavaScript还提供了三个特殊的引用类型：String/Number/Boolean。

基本包装类型：把基本类型包装成复杂类型。

```javascript
var str = “abc”;
var result = str.indexOf(“a”);
//发生了三件事情
1. 把简单类型转换成复杂类型：var s = new String(str);
2. 调用包装类型的indexOf方法：var result = s.indexOf(“a”);
3. 销毁刚刚创建的复杂类型（过河拆桥、卸磨杀驴）
```



# 补充

## 递归函数

> 递归函数：自己直接或者间接调用自己的函数，递归函数一定要留有出口，不然就是死循环了

递归函数比较抽象，尤其是第一次接触的同学们，大家了解即可。

```javascript
1. 求1-100所有数的和

2. 斐波那契数列
```



## 回调函数

> 回调函数：把函数当成参数来使用，那么这个函数就叫回调函数。

跟递归一样，回调函数现阶段只要求了解概念即可，在特效的时候，会用到回调函数，到时候再解释一下。



## arguments对象

>JavaScript中，arguments对象是比较特别的一个对象，实际上是当前函数的一个内置属性。也就是说所有函数都内置了一个arguments对象，arguments对象中存储了传递的所有的实参。arguments是一个伪数组，因此及可以进行遍历

```javascript
//1. 求任意个数的最大值
//2. 求任意个数的和
```



## json对象

> JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式，采用完全独立于语言的文本格式，是理想的数据交换格式。同时，JSON是 JavaScript 原生格式，这意味着在 JavaScript 中处理 JSON数据跟处理对象是一样的。


JSON的属性必须用双引号引号引起来，对象字面量可以省略

```javascript
//对于js对象来说，属性名的双引号是可以省略的。
var obj = {
  name:"zs",
  age:18,
  sex:"男"
}

//json对象的属性名必须使用双引号括起来
var obj = {
  "name":"zs",
  "age":18,
  "sex":"男"
}

//在js中，其实就可以把json当成javascript的对象，因此操作是一样。
```







