# 記憶體面版 - 記憶體堆快照 1
今天我們要開始一起來討論記憶體面版 (Memory panel)，這個面版的主要功能就是讓你做網站的記憶體體檢，像是記憶體洩漏、記憶體膨脹和頻繁的垃圾回收都可以透過這個面版來做檢測。這個面版牽扯到很多記憶體相關的術語，很多我也不是很熟悉，如果你想要深入的了解這個主題，我強烈建議大家可以在看完這個幾天的文章後，再到官方[文件](https://developers.google.com/web/tools/chrome-devtools/memory-problems/) 把記憶體這個區塊看完，如果你只是想要了解開發者工具如何檢測網站的記憶體使用狀況，那讀完這幾天的文章後，我相信你會有個基本的了解。

接下來這幾天我們的進展速度也會比較慢一點，效能面版 (Performance panel) 我們可能是沒有機會詳細介紹了冏，但是希望在討論記憶體檢測時，我們可以至少看一下如何透過它來幫助我們檢測。

## 使用記憶體面版
請先打開 Chrome 開發者工具然後切換到記憶體面版 (Memory panel)，一進來之後你會看到幾個選項：
- Take heap snapshot
- Record allocation profile
- Record allocation timeline

![記憶體面版介面擷圖](https://www.dropbox.com/s/9wxhv3fm5gvjb6y/memory.jpg?raw=1)
**圖 1** : 記憶體面版介面

我們今天先從 **Take heap snapshot** 開始介紹，這邊的 **heap snapshot** 官方翻成 **堆快照**，我們今天及接下來幾天使用的範例都是官方文件給的範例，為了方便大家操作，我把這幾個範例都放在 Codepen.io 上，今天使用的範例在[這裡](https://codepen.io/konekoya/pen/vpyqby?editors=1010)

在開始之前，我們先來看一下我們這個範例在做什麼：

JavaScript
```js

var detachedNodes;

function create() {
  var ul = document.createElement('ul');
  for (var i = 0; i < 10; i++) {
    var li = document.createElement('li');
    ul.appendChild(li);
  }
  detachedTree = ul;
}

document.getElementById('create').addEventListener('click', create);

```

HTML
```html
<button id="create">Create detached List</button>
```

從上面的範例程式可以看到，在 JavaScript 裡我們用了一個 `create` 方法來創造 10 個 `li` 並把它 `append` 到一個 `ul` 裡成為一組新的清單，最後我們把它綁到一個 `button` 元素上，所以每一次只要按下這個按鈕，它就會產生一組 DOM 清單。但在看完程式後有沒有發現其實這些產生出來的清單並沒有真的 `append` 到 DOM 樹裡，它只有把它創造出來，然後指到 `detachedTree` 這個變數裡。

好，會這樣做的原因是因為接下來我們要做的是檢測 DOM 樹裡的已分離節點 `Detached nodes`, 而我們上面的程式就會產生所謂的已分離節點，這些節點已經從 DOM 樹中被分離，但是仍然被 JavaScript 引用，所以會造成記憶體洩漏 (Memory leaks)。

## 小結
我們今天就先停在這裡，明天我們會使用開發者工具來檢測這些已分離節點。在這裡也想先跟大家說明，記憶體檢測及除錯已經算是蠻困難的除錯技巧，問題可能很容易找到，但是修正它是有一定的難度，所以如果沒辦法修好也不要太難過XD，這需要時間練習。好，不多說廢話XD，今天就先這樣子啦！
