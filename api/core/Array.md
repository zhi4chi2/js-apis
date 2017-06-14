构造函数：
* new Array() - 返回空数组 [] ， length = 0
* new Array(size) - size 是期望的数组元素的个数，当 size 是负数或者大于 2<sup>32</sup> - 1 ，将抛出 RangeError 异常。
* new Array(element0, element1, ..., elementn)


属性：
* length - 可读写。


方法：
* concat() - 不修改原数组
* join()
* pop()
* push()
* reverse()
* shift()
* slice() - 不修改原数组
* sort()
* splice()
* toLocaleString()
* toString()
* unshift()


# join()

把数组的所有元素连接成字符串，缺省的连接符是逗号。


```javascript
var a = ['a', 'b'];
a.join(); // "a,b"
a.join(', '); // "a, b"

var a = [ 1, [ 2, [ 'a', 'c' ] ] ];
a.join(); // 1,2,a,c
```
join() 会递归展开子数组。


# reverse()

reverse 在原数组上操作，更改了原数组。

```javascript
var a = ['a', 'b'];
a.reverse(); // ["b", "a"]
a; // ["b", "a"]
```


# sort()

sort 在原数组上操作，更改了原数组。默认使用字母顺序排序。

```javascript
var a = ['z', , 'a'];
a.sort(); // ["a", "z", undefined]
a; // ["a", "z", undefined]
```
undefined 被排在最后。


自定义排序方式：

```javascript
var a = [ 33, 4, 1111, 222 ];
a.sort();
a; // [1111, 222, 33, 4]

a.sort(function(x, y) {
  return x - y;
});
a; // [4, 33, 222, 1111]
```


# concat()

返回新数组（不修改原数组），包含原数组和所有参数。如果某个参数是数组，将被展开，但不能递归展开。

```javascript
var a = [ 1, 2, 3 ];
a.concat(4, 5); // [1, 2, 3, 4, 5]
a; // [1, 2, 3]

a.concat([ 4, 5 ]); // [1, 2, 3, 4, 5]

a.concat([ 4, [ 5, 6 ] ]); // [1, 2, 3, 4, [5, 6]]
```


# slice()

返回数组的一个片段（子数组），不修改原数组。

```javascript
var a = [ 1, 2, 3, 4, 5 ];
a.slice(0, 3); // [1, 2, 3]
a; // [ 1, 2, 3, 4, 5 ]

a.slice(1, -1); // [2, 3, 4]
```

负数索引表示 length + 索引值，例如 -1 表示最后一个元素（索引值 length - 1 ）。


另外在 jQuery 中经常使用这个方法将非数组转为数组：

```javascript
var obj = {};
obj[1] = 'x';
obj[3] = 'y';
obj.length = 3;
var array = Array.prototype.slice.call(obj);
console.log(array); // [undefined, "x", undefined]
```


# splice()

插入或删除数组元素，修改原数组。参数：
1. 插入或删除的位置
1. 要删除的元素个数，如果省略，则一直删到末尾
1. 剩下的参数都是要插入的元素。'''插入后元素的顺序和参数的顺序一致'''，即这些参数是被同时插入的，而不是逐个插入的。
返回删掉的片段。


```javascript
var a = [ 1, 2, 3, 4, 5 ];
a.splice(4); // [5]
a; // [1, 2, 3, 4]

a.splice(2, 0, 'a', 'b'); // []
a; // [1, 2, "a", "b", 3, 4]

a.splice(2, 2, [ 1, 2 ], 3); // ['a', 'b']
a; // [1, 2, [1, 2], 3, 3, 4]
```
splice() 不会展开插入的数组元素。


# push()/pop()

push 将一个或多个元素插入到数组的尾部，并返回新数组的长度。 pop 删除数组的最后一个元素，返回删除的元素。 push/pop 直接修改原数组。

```javascript
var a = [];
a.push(1, 2); // 2
a; // [1, 2]

a.pop(); // 2
a; // [1]

a.push([ 4, 5 ]); // 2
a; // [1, [4, 5]]
a.pop(); // [4, 5]
a; // [1]
```


# unshift()/shift()

unshift()/shift() 与 push()/pop() 的不同在于它是在数组的头部操作，而不是在尾部。 unshift/shift 直接修改原数组。

```javascript
var a = [];
a.unshift(1, 2); // 2
a; // [1, 2]

a.shift(); // 1
a; // [2]

a.unshift([ 4, 5 ]); // 2
a; // [[4, 5], 2]

a.shift(); // [4, 5]
a; // [2]
```
注意： unshift() 与 splice() 一样，在插入时是把参数同时插入的，而不是逐个插入的。


# toString()/toLocaleString()

注意， toString 生成的字符串中没有方括号。** toString() 相当于无参数调用 join()**


```javascript
var a = [ 1, 2 ];
a.toString(); // 1,2

a = [ 1, [ 2, [ 'a', 'c' ] ] ];
a.toString(); // 1,2,a,c
```
