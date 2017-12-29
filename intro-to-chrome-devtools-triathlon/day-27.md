# 記憶體面版 - 使用記憶體分配時間線
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

![進行中的檢測](https://www.dropbox.com/s/juu7o7wwvun4ej9/recording.jpg?raw=1)
**圖 1** : 正在進行中的檢測

這個工具跟我們前兩天用的記憶堆快照 (Heap snapshot) 有點不太一樣，就像它的名稱一樣，它是在**錄制 (Record)** 我們在頁面上的操作，然後等錄制完後再來查看我們的記憶體洩漏問題。所以現在我們的時間線會一直跑直到我們按下工具列上的停止按鈕。現在按幾次我們頁面上的 **Create memory leaks** 按鈕來產生記憶體洩漏，然後再按下停止按鈕來停止錄制。

這是我錄制完的快照：
![進行中的檢測]()

我們的快照會不一樣，但是你應該可以在你的快照中看到幾條特別長的藍色線條，這些就是我們剛剛透過 `grow` 方法產生的超大陣列。當你點下那個藍色線條後，你會發現 **Shallow Size** 跟 **Retained Size** 的建構子 (Constructor) 都是 **string**，請展開 **string**，你會在裡面看到裡面有一堆 **xxxxx...** 的 string，然後在下方的 **Object** 裡可以看到它詳細的資料，這裡我們可以看到 `x` 這個變數是在 `window` 這個物件下。

> 這個時間軸的操控方法跟網路面版的一樣

## 小結
今天我們就很簡單的講了一下如何操作記憶體分配時間線，透過它來找出記憶體洩漏的問題。其實如果你拿我們前兩天的範例來跑也是可以在這邊看到，但是需要把產生的 `li` 數量變多一點，這樣在這個時間線裡才會比較容易看的清楚 (吃的記憶體小，藍的線條就會變的很小條到甚至看不到)，接下來，我們要把記憶體面版裡的最後一個功能講完，然後我們還有一天的時間，我想要來介紹效能 (Performance panel) 面版，它的記憶體檢測工具也很方便，跟我們這幾天使用的方式不太一樣，所以我想我們還是要花點時間一起討論一下。

