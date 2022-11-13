---
title: JavaScript的一些分享
date: 2022-08-15 11:41:10
categories:tags: ['JavaScript']
tags: ['js','分享']
---

## 2022年你需要了解的 13 种 JavaScript 代码技巧

### 分享一些我常用的代码优化技巧，希望对你有帮助。

#### 1.多表达式多 if 判断

**我们可以在数组中存储多个值，并且可以使用数组include方法。**

~~~javascript
// 长
if (x === 'abc' || x === 'def' || x === 'ghi' || x ==='jkl') {
  //logic
}
// 短
if (['abc', 'def', 'ghi', 'jkl'].includes(x)) {
  //logic
}
~~~

####  2.简写 if else

**如果 if-else 的逻辑比较降低，可以使用下面这种方式镜像简写，当然也可以使用三元运算符来实现。**

~~~javascript
// 长
let test: boolean;
if (x > 100) {
  test = true;
} else {
  test = false;
}
// 短
let test = (x > 10) ? true : false;
// 也可以直接这样
let test = x > 10;
~~~

#### 2.合并变量声明

**当我们声明多个同类型的变量时，可以像下面这样简写。**

~~~javascript
// 长 
let test1;
let test2 = 1;
// 短 
let test1, test2 = 1;
~~~

#### 3.合并变量赋值

**当我们处理多个变量并将不同的值分配给不同的变量时，这种方式非常有用。**

~~~javascript
// 长 
let test1, test2, test3;
test1 = 1;
test2 = 2;
test3 = 3;
// 短 
let [test1, test2, test3] = [1, 2, 3];
~~~

#### 5.&& 运算符

如果仅在变量值为 true 的情况下才调用函数，则可以使用 && 运算符。

~~~javascript
// 长 
if (test1) {
 callMethod(); 
} 
// 短 
test1 && callMethod();
~~~

#### 6. 箭头函数

~~~javascript
// 长  
function add(a, b) { 
   return a + b; 
} 
// 短 
const add = (a, b) => a + b;
~~~

#### 7. 短函数调用

**可以使用三元运算符来实现这些功能。**

~~~javascript
const fun1 = () => console.log('fun1');
const fun2 = () => console.log('fun2');
// 长
let test = 1;
if (test == 1) {
  fun1();
} else{
  fun2();
}
// 短
(test === 1? fun1:fun2)();
~~~

#### 8. Switch 简记法

**我们可以将条件保存在键值对象中，并可以根据条件使用。**

~~~javascript
// 长
switch (data) {
  case 1:
    test1();
  break;

  case 2:
    test2();
  break;

  case 3:
    test();
  break;
  // And so on...
}

// 短
const data = {
  1: test1,
  2: test2,
  3: test
};

data[something] && data[something]();
~~~

#### 9. 默认参数值

~~~javascript
// 长
function add(test1, test2) {
  if (test1 === undefined)
    test1 = 1;
  if (test2 === undefined)
    test2 = 2;
  return test1 + test2;
}
// 短
const add = (test1 = 1, test2 = 2) => (test1 + test2);
~~~

#### 10. 扩展运算符

~~~javascript
// 长-合并数组
const data = [1, 2, 3];
const test = [4 ,5 , 6].concat(data);
// 短-合并数组
const data = [1, 2, 3];
const test = [4 ,5 , 6, ...data];

// 长-拷贝数组
const test1 = [1, 2, 3];
const test2 = test1.slice()
// 短-拷贝数组
const test1 = [1, 2, 3];
const test2 = [...test1];
~~~

#### 11. 模版字符串

~~~javascript
// 长
const welcome = 'Hi ' + test1 + ' ' + test2 + '.'
// 短
const welcome = `Hi ${test1} ${test2}`;
~~~

##### 12. 简写对象

~~~javascript
let test1 = 'a'; 
let test2 = 'b';
// 长 
let obj = {test1: test1, test2: test2}; 
// 短 
let obj = {test1, test2};
~~~

#### 13. 在数组中查找最大值和最小值

~~~javascript
const arr = [1, 2, 3]; 
Math.max(…arr); // 3
Math.min(…arr); // 1
~~~

