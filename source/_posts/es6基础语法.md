---
title: ES6基础语法
date: 2018-02-03 16:55:10
tags: ES6
categories: [ES6]
---

### ECMAScript 6 简介
ECMAScript 6.0 简称ES6,是JavaScript语言的下一代标准,ECMAScript 就是JavaScript的语法规范,
### 环境搭建
目前为止,因为低版本的浏览器还不支持ES6,所以如果我们使用ES6,我们需要搭建一个开发环境,能让ES6转换成ES5, 这里面的环境搭建可以参考网上的一些教程,也可以使用webpack,它可以自动编译
<!--more-->
### 新加的声明方式 let  const
####let
 1. let 只在命令所在的代码块中有效 ( 局部变量)  也就是只在`{}`中有用
 ```javascript
 {
 let a=1;
 var b=2;
 console.log(a);  // 1
 }
 console.log(a);  // a is no defied 
 console.log(b);  // 2
 ```
  ```javascript
 var a=[];
 for(let i=0;i<10;i++){
    a[i]=function(){ //i=6
        console.log(i)
    };
 }
 a[6]();  //6
 ```
2. `for`循环的特别之处,循环变量是一个父作用域,而循环体内部是一个子作用域
```javascript
for(let i=0;i<3;i++){//父作用域
    let i='abc';  //子作用域
    console.log(i);
}
//abc
//abc
//abc
```

3. 暂时性死区(TDZ) 只要块级作用域存在`let`,那么它所声明的变量就只能在这个作用域中起作用,不受外部的影响,在声明变量之前,该变量是不可用的,所以要先声明后使用
```javascript
 {
 let a;
 console.log(a);  //undefined
 a=22;
 console.log(a); //22
 }
 ```


4. 不能重复声明 在相同的作用域内,只能声明一次 ,函数内部不能重新声明参数
```javascript
function fn(arg){
let arg ;  //报错
}
function fn(arg){ {
  let arg;  // 不报错
  }
 }
```
#### const 只读常量 一旦声明,将不能改变
1. 和let 相似
2. 传址赋值在赋值的过程中,变量实际上存储的是数据的地址(对数据的引用),而不是原始的数据
 ```javascript
 const person = {"name":"张三"};
 person.name ="李四";
 person.age=20;
 console.log(person);
 // 输出 {name:"李四",age:20}
 ```
 例子:你预约了一位王师傅装修,你把地址给了他,他顺着地址来你家把门染成红色,结果过了两天,你不满意,就预约了李师傅,给了他地址,他把门涂成了绿色,到最后不管是哪个师傅来,门都是绿色,
 ```
//王师傅把家门染成红色
let wang ={'door':'red'};
//你把地址给了李师傅
let li = wang;
//李师傅把门染成了绿色
li.door = green;
//最后不管谁来都是绿色
console.log(wang);
console.log(li);
 ```

### 变量的解构赋值 
####   数组的解构赋值 (次序)
1. `匹配模式`左右两边模式相同,左边就会被赋予相应的值
```javascript
let [a,b,c]=[1,2,3]
console.log(a);  //1
console.log(b);  //2
console.log(c);   //3
```
2. 可以指定默认值
```
let [x,y='0']=['1'];//x='1',y='0'
```
ES6使用严格运算符(===),只有是`undefined`,默认值才能生效
```javascript
let [x=1] = [undefined];
x  //输出1;
let [x=1] = [null];
x  //输出null
```
#### 对象的解构赋值
1. 与次序无关,变量和属性同名才能赋值
```javascript
let [foo,baz,bar]=[foo:'a',bar:'b'];
foo   //输出 a
bar   //输出 b
baz   //输出 undefined
```
2. 赋值的是变量而不是属性
```javascript
let {foo:baz} = {foo:'aaa',bar:'bbb'}
baz  //aaa
foo  //error: foo is not defined
```
3. 嵌套结构
```javascript
let obj = {
    p:['hallo',{y:'world'}]
};
let {p,p:[x,{y}]} = obj;
x   // hello
y   // world
p   // ['hallo',{y:'world'}]
```
#### 字符串的解构赋值
字符串也可以解构赋值。这是因为此时，字符串被转换成了一个类似数组的对象。
```javascript
const [a, b, c, d, e] = 'hello';
a // "h"
b // "e"
c // "l"
d // "l"
e // "o"
```
### 模板字符串
#### 字符串的拼接 ` `${}` `
```javascript
//传统拼接
let name = 'jack';
let foo = 'he is'+name+' '; //he is jsck
//ES6拼接
let name ='jack';
let foo =`he is ${name}`;
```
#### 可以定义多行字符串
```javascript
let str = `today is 
very happy`

//today is
//very happy
//所有的空格和缩进被保留,如果需要使用`符号,前面加\进行转义
```
#### ${ }里面可以放任何javascript表达式
运算表达式
```javascript
let a=1;
let b=2;
let str = `the sum is ${a+b}`;
// the num is 3
```
对象属性
```javascript
let obj = {'a':1,'b':2};
let str = `the sum is ${obj:a+obj:b}`;
// the num is 3
```
函数调用
```javascript
function fn (){
    return 3
}
`the sum is ${fn()}`
//the sum is 3

```

