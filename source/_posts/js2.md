---
title: js第二天
tags: [笔记,随笔,美文]
categories: 笔记
---




# 循环语句

> 在javascript中，循环语句有三种，while、do..while、for循环。

## while循环

基本语法：

```javascript
//当循环条件为true时，执行循环体，
//当循环条件为false时，结束循环。
while(循环条件){
  //循环体
}
```

代码示例：

```javascript
//计算1-100之间所有数的和
//初始化变量
var i = 1;
var sum = 0;
while(i <= 100){//判断条件
  sum += i;//循环体
  i++;//自增
}
console.log(sum);
```



## 断点调试

>断点调试是指自己在程序的某一行设置一个断点，调试时，程序运行到这一行就会停住，然后你可以一步一步往下调试，调试过程中可以看各个变量当前的值，出错的话，调试到出错的代码行即显示错误，停下。

调试步骤：

```javascript
浏览器中按F12-->sources-->找到需要调试的文件-->在程序的某一行设置断点
```



调试中的相关操作：

```javascript
Watch:监视，通过watch可以监视变量的值的变化，非常的常用。
F10:程序单步执行，让程序一行一行的执行，这个时候，观察watch中变量的值的变化。
F8：跳到下一个断点处，如果后面没有断点了，则程序执行结束。
```

tips: ***监视变量，不要监视表达式，因为监视了表达式，那么这个表达式也会执行。***

苦口婆心一下：

<font color="red">

1. 代码调试的能力非常重要，只有学会了代码调试，才能学会自己解决bug的能力。初学者不要觉得调试代码麻烦就不去调试，知识点花点功夫肯定学的会，但是代码调试这个东西，自己不去练，永远都学不会。
2. 今天学的代码调试非常的简单，只要求同学们记住代码调试的这几个按钮的作用即可，后面还会学到很多的代码调试技巧。

</font>



## do..while循环

> do..while循环和while循环非常像，二者经常可以相互替代，但是do..while的特点是不管条件成不成立，都会执行一次。

基础语法：

```javascript
do{
  //循环体;
}while(循环条件);
```

代码示例：

```javascript
//初始化变量
var i = 1;
var sum = 0;
do{
  sum += i;//循环体
  i++;//自增
}while(i <= 100);//循环条件
```



思考：

```
1. 循环输入账号密码的案例用do..while怎么写？
2. 循环表白的案例用do..while怎么写？
```



## for循环（重点）

>  写while循环的经常会忘记自增，for循环其实是while循环演化过来的，语法更加的简洁明了，使用非常的广泛。

for循环语法：

```javascript
//主要for循环的表达式之间用的是;号分隔的，千万不要写成,
for(初始化表达式;判断表达式;自增表达式){
  //循环体
}
```



执行顺序：1243  ----  243   -----243(直到循环条件变成false)

1. 初始化表达式
2. 判断表达式
3. 自增表达式
4. 循环体



for循环代码示例：

```javascript
//计算1-100之间所有数的和
var sum = 0;
for(var i = 1; i <= 100; i++){
  sum += i;
}
```



思考1：

```
1 求1-100之间所有数的和、平均值
2 求1-100之间所有数的乘积
3 计算1-100之间能3整除的数的和
4 计算1-100之间不能被7整除的数的和
```



思考2：

```
5 求1-100之间所有偶数的和
6 求1-100之间所有奇数的和
7 同时求1-100之间所有偶数和奇数的和
```



思考3：

```
1 打印正方形
2  打印直角三角形
3 打印9*9乘法表
```



思考4：

```
1. 本金10000元存入银行，年利率是千分之三，每过1年，将本金和利息相加作为新的本金。计算5年后，获得的本金是多少？
2. 有个人想知道，一年之内一对兔子能繁殖多少对？于是就筑了一道围墙把一对兔子关在里面。已知一对兔子每个月可以生一对小兔子，而一对兔子从出生后第3个月起每月生一对小兔子。假如一年内没有发生死亡现象，那么，一对兔子一年内（12个月）能繁殖成多少对？ 
   兔子的规律为数列，1，1，2，3，5，8，13，21

```



## break和continue

> break:立即跳出整个循环，即循环结束，开始执行循环后面的内容（直接跳到大括号）
>
> continue:立即跳出当前循环，继续下一次循环（跳到i++的地方）



思考1：

```javascript
//输出结果是什么？
for(var i = 1; i <=10; i++) {
  if(i == 5){
    continue;
  }
  
  if(i == 7){
    break;
  }
  console.log(i);
}
```



思考2：

```
1. 求1-100之间不能被7整除的整数的和（用continue）
2. 求200-300之间所有的奇数的和（用continue）
3. 求200-300之间第一个能被7整数的数（break）
```



## 总结

1. 循环有很多种，但是以后用得最多的是for循环
2. 当不明确循环次数的时候，可以使用while循环
3. 当无论如何都要执行一次代码的时候，可以使用do..while循环。
4. 循环可以相互替代。



# 数组

> 所谓数组，就是将多个元素（通常是同一类型）按一定顺序排列放到一个集合中，那么这个集合我们就称之为数组。

思考：

```
为什么要有数组？
1. 我们知道，一个变量能够存储一个值，当我们想要存储多个值的时候，就可以使用数组。比如存储一个班级里面所有学生的姓名。
2. 使用数组可以对多个相同类型的值统一的管理，存储起来方便，操作的时候也会很方便。
```

## 创建数组

> 在javascript数组是一个有序的列表，可以在数组中存放任意的数据，并且数组的长度可以动态的调整。



通过构造函数创建数组

```
var arr = new Array();//创建了一个空数组
var arr = new Array("zs","ls","ww");//创建了一个数组，里面存放了3个字符串
var arr = new Array(1,2,3,4);//创建了一个数组，里面存放了4个数字
```



通过数组字面量创建数组

```
var arr1 = []; //创建一个空数组
var arr2 = [1, 3, 4]; //创建一个包含3个数值的数组，多个数组项以逗号隔开
var arr3 = ["a", "c"]; // 创建一个包含2个字符串的数组
```



## 数组的下标与长度

数组的下标：数组是有序的，数组中的每一个元素都对应了一个下标，***下标是从0开始的***

```
var arr = ["zs", "ls", "ww"];
arr[0];//下标0对应的值是zs
arr[3];//下标3对应的值是ww
```

数组的长度：跟字符串一样，数组有一个length属性，指数组中存放的元素的个数。

```
var arr = ["zs", "ls", "ww"];
arr.length;//这个数组的长度是3
//空数组的长度是0
```

下标与长度的关系：最大的下标 = length - 1



## 数组的赋值与取值

数组的取值

```
//格式：数组名[下标]
//功能：获取数组对应下标的那个值，如果下标不存在，则返回undefined。
var arr = ["red", "green", "blue"];
arr[0];//red
arr[2];//blue
arr[3];//这个数组的最大下标为2,因此返回undefined
```



数组的赋值

```javascript
//格式：数组名[下标] = 值;
//如果下标有对应的值，会把原来的值覆盖，如果下标不存在，会给数组新增一个元素。
var arr = ["red", "green", "blue"];
arr[0] = "yellow";//把red替换成了yellow
arr[3] = "pink";//给数组新增加了一个pink的值
```

思考：如何给一个数组增加新的元素？

```
1. 把1-100之间所有的数，放到数组中
2. 把1-100之间所有的奇数，放到数组中
3. 把1-100之间能被3整数的数字，存到数组中
```







## 数组的遍历

> 遍历：遍及所有，对数组的每一个元素都访问一次就叫遍历。

数组遍历的基本语法：

```
for(var i =0; i < arr.length; i++) {
	//数组遍历的固定结构
}
```



思考1：

```
var arr = [298, 1, 3, 4, 6, 2, 23, 88,77,44];
1 求一组数中的所有数的和跟平均值
2 求一组数中的最大值
3 求一组数中的最小值和最小值所在的位置
4 求一组数中的最大值和最小值以及所在位置
```



思考2：

```
var arr = ["a", "bb","ccc","dddd"];
1 将字符串数组用|或其他符号分割
2 有一个字符串数组，求字符串数组中每项的长度，并把长度的数值存储到新的数组中
3 将数组中值为0的项去掉，将不为0的值存入一个新的数组
4 让一个数组倒叙保存另一个数组中的每一项
```



# 冒泡排序

1. 初级版本
2. 中极版本
3. 完成版本



<font color="red">声明：我们今天主要是学习数组遍历的语法，对于这种数学烧脑类的题目，想不到是很正常的</font>

【数组去重】

【计算一个数是几位数】

【将12345转换成54321】













