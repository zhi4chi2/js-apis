继承 Object 。

---
构造函数：
* new Number(value)
* Number(value)

其中 value 是要创建 Number 对象的数值，或者要转换为数字的值。


---
方法：
* toFixed - 不使用指数表示法，指定小数点后的位数。有可能四舍五入。
* toExponential - 使用指数表示法，指定小数点后的位数（小数点前固定为一位数字）。有可能四舍五入。
* toPrecision - 指定有意义的位数，如果指定的位数不足以显示所有整数部分，则使用指数表示法。有可能四舍五入。


---
```javascript
var n = 123456.789;
n.toFixed(0); // 123457
n.toFixed(2); // 123456.79
n.toExponential(1); // 1.2e+5
n.toExponential(3); // 1.235e+5
n.toPrecision(4); // 1.235e+5
n.toPrecision(7); // 123456.8
```
