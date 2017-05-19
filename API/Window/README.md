浏览器端的 Window 对象。


#confirm

confirm 弹出的对话框会阻塞浏览器的事件处理，一直等待用户做出选择，然后会返回 true/false 。这一点没有东西可以替代它。

jQuery ui 的 dialog 不会阻塞。 showModalDialog, setTimeout 也都不会阻塞 javascript 继续执行。

网络上关于 “javascript 模拟 confirm” 都只是模拟对话框而已，不能阻塞 javascript 的执行。
