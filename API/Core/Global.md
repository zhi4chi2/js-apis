# setTimeout

setTimeout 不会阻塞 javascript 代码继续执行。

```javascript
function showTime() {
    var today = new Date();
    console.log("The time is: " + new Date().getTime());
    setTimeout(showTime, 5000);
    console.log("now is: " + new Date().getTime());
}
// The time is: 1416553159413
// now is: 1416553159419
// The time is: 1416553164421
// now is: 1416553164423
// The time is: 1416553169430
// now is: 1416553169433
showTime();
```
