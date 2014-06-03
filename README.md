es6-info
========

> [兼容性检查](http://kangax.github.io/compat-table/es6/) 建议用ff测试一些case


#### 如果开启？

1. chrome开启：

chrome://flags/ 搜索harmony，开启就可以



#### const

用来声明常量，而且声明后的不能改变同时只在块级作用域有效




#### Iterator

是一种协议，部署next的方法，包含：

1. value属性: 是当前遍历位置的值
2. done属性: 是boolean值，表示是否遍历结束

举例：

```shell
function idMaker() {
	var index = 0;
	return {
		next: function() {
			return {
				value: index++,
				done: false
			}
		}
	}
}

var id = idMaker();

id.next().value;
id.next().value;
id.next().value;
```


#### for of

具有iterator接口的，可以用for of来遍历


```shell
var arr = ['zhang', 'yao', 'chun'];
for (let n of arr) {
	console.log(n);
}
```


#### generator函数

内部状态的遍历器，每调用一次，内部的状态会发生改变

特征:

1. function关键字后面有一个星号
2. 函数体内部有yield语句，定义遍历器的成员（不同的内部状态）


代码：

```shell
function* myGenerator() {
	yield 'zhang';
	yield 'yao';
	yield 'chun';
}

var g = myGenerator();
g.next(); //{value: "zhang", done: false}
g.next(); //{value: "yao", done: false}
g.next(); //{value: "chun", done: false}
g.next(); //{value: undefined, done: true}
```

总结：

1. 调用generator函数，函数并不执行，而是返回遍历器（Iterator）
2. 调用next方法，遍历yield语句定义的内部状态

generator提供一种可以暂停执行的函数，yield语句就是暂停标志,next方法遇到yield后，就会暂停执行后面的操作，并将跟在yield后面的那个表达式的值赋给返回对象的value属性。


所以可以用generator函数来作lazy


```shell
function* log() {
	console.log('I am zhangyaochun');
}

var generator = log();

setTimeout(function(){
	generator.next();
}, 4000);
```






