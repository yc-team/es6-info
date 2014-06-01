es6-info
========

> [兼容性检查](http://kangax.github.io/compat-table/es6/)

#### Iterator

是一种协议，部署next的方法，包含：

1. value属性是当前遍历位置的值
2. done属性是boolean值，表示是否遍历结束

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
const arr = ['zhang', 'yao', 'chun'];
for (let n of arr) {
	console.log(n);
}
```









