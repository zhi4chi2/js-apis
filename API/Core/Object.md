# constructor
每个 JS 对象都有一个 constructor 属性，它引用初始化这个对象的函数。
```javascript
var d = new Date();
d.constructor === Date; // true
```


确定一个未知值的类型：
```javascript
if ((typeof o == 'object') && (o.constructor == Date)) {
  // o 是 Date 的实例，不能是 Date 子类的实例
}
if ((typeof o == 'object') && (o instanceof Date)) {
  // o 是 Date 或 Date 子类的实例
}
```


# toString()
Object.toString() 默认返回 "[object Object]" ，子类可以自定义自己的 toString() 。比如 Array 返回列表， Function 返回源代码。


# toLocaleString()
Object.toLocaleString() 默认与 Object.toString() 相同。子类（比如 Date, Number, Array ）可以自定义。


# valueOf()
Object.valueOf() 返回自身。子类（比如 Date ）可以自定义返回基本类型值。


# hasOwnProperty()
如果属性不是继承来的，则返回 true ，否则返回 false 。
```javascript
var o = {
  x : "a",
  y : "b"
};

o.hasOwnProperty('x'); // true
o.hasOwnProperty('constructor'); // false
o.hasOwnProperty('toString'); // false
```


# propertyIsEnumerable()
如果属性'''不是继承来的'''，并且可用 for/in 枚举，则返回 true ，否则 false 。
```javascript
var o = {
  x : "a",
  y : "b"
};

o.propertyIsEnumerable('x'); // true
o.propertyIsEnumerable('constructor'); // false
o.propertyIsEnumerable('toString'); // false
```


注意，如果属性是继承而来的，返回 false 。所以这个方法与 hasOwnProperty() 结果基本一致。
```javascript
function A() {
  this.x = 'x';
}
var a = new A();
A.prototype.y = 'y';

console.log(a.propertyIsEnumerable('x')); // true
console.log(a.propertyIsEnumerable('y')); // false

console.log('y' in a); // true

for ( var p in a) {
  console.log(p); // x, y
}
```


# isPrototypeOf()
如果 a 是 b 的原型，则 a.isPrototypeOf(b) = true

```javascript
var o = {};

Object.prototype.isPrototypeOf(o); // true
Object.isPrototypeOf(o); // false
Function.prototype.isPrototypeOf(Object); // true
```
