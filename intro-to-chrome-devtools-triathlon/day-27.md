# 記憶體面版 - 檢測記憶體洩漏
今天我們要透過記憶體面版的另一個工具來檢測記憶體洩漏的這個問題，先來看一下今天我們要用來檢測的程式：

> 今天的測試程式範例一樣來自[官方文件](https://developers.google.com/web/tools/chrome-devtools/memory-problems/)，而我也把範例程式放到 Codepen.io 上了，想要跟著一起做的朋友可以點[這裡](https://codepen.io/konekoya/pen/LeWVbO)

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

> 你可以把我們上面這一段程式貼到控制台面版裡測試看看會得到什麼結果


## 使用記憶體分配時間線 (Record allocation timeline)

好，我們已經準備好程式了，現在讓我們打開 Chrome 開發者工具，然後切換到記憶體面版 (Memory panel)，然後選擇 **Record allocation timeline**，再按下 **Start** 按鈕，這樣檢測工作就會開始了，你的畫面應該會是像下圖：

![進行中的檢測]()

這個工具跟我們前兩天用的記憶堆快照 (Heap snapshot) 有點不太一樣，就像它的名稱一樣，它是在**錄制 (Record)** 我們在頁面上的操作，然後等錄制完後再來查看我們的記憶體洩漏問題。所以現在我們的時間線會一直跑直到我們按下工具列上的停止按鈕。
