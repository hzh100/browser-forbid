
# browser-forbid
> 浏览器  **JS 禁止F12和右键操作控制台，兼容各浏览器**

>在网上也找一些博客文章，都还不错。不过在亲测下来发现不需要那么的麻烦。只需要简单的几行代码就可以。以下代码是整理后并测试过的禁止鼠标右键菜单和F12打开控制台看源码

## 1. 鼠标点击事件

```js
document.onmousedown = function mdClick(event) {
  var e = event || window.event || arguments.callee.caller.arguments[0];
  if (e.button == 2 || e.button == 3) {
    alert("你愁啥!!!");
  }
}
```

## 2. 禁用浏览器 默认右键菜单

```js
document.oncontextmenu = new Function("return false;");
```

## 3. 监听键盘事件

```js
document.onkeydown = document.onkeyup = document.onkeypress = function(event) {
  var e = event || window.event || arguments.callee.caller.arguments[0];

  if (e && e.keyCode == 123) {
    alert("你愁啥!!!");
    e.returnValue = false;
    return (false);
  }
}

```