# 記憶體面版 - 檢測記憶體洩漏
今天我們要透過記憶體面版的另一個工具來檢測記憶體洩漏的這個問題，先來看一下今天我們要用來檢測的程式：

> 今天的測試程式範例一樣來自[官方文件](https://developers.google.com/web/tools/chrome-devtools/memory-problems/)

```js
var x = [];

function grow() {
  x.push(new Array(1000000).join('x'));
}

document.getElementById('grow').addEventListener('click', grow);
```

```html
<button id="grow">Create memory leaks</button>
```

