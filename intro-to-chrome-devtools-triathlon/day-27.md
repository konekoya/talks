# 記憶體面版 - 檢測記憶體洩漏
今天我們要透過記憶體面版的另一個工具來檢測記憶體洩漏的這個問題，先來看一下今天我們要用來檢測的程式：

> 今天的測試程式範例一樣來自[官方文件](https://developers.google.com/web/tools/chrome-devtools/memory-problems/)

JavaScript
```js
var x = [];

function grow() {
  x.push(new Array(1000000).join('x'));
}

document.getElementById('grow').addEventListener('click', grow);
```

HTML
```html
<button id="grow">Create memory leaks</button>
```

在這段程式中，我們定義了一個 `grow` 方法，這個方法會產生一百萬個字串 x 並放到 `x` 這個變數裡，然後我們把 `grow` 這個方法綁定到 `Create memory leaks` 這個按鈕的 `click` 事件上，方便們之後可以透過點擊這個按鈕來呼叫 `grow` 方法
