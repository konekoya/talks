# 記憶體面版
今天我們要開始一起來討論記憶體面版 (Memory panel)，這個面版的主要功能就是讓你做網站的記憶體體檢，像是記憶體泄漏、記憶體膨脹和頻繁的垃圾回收都可以透過這個面版來做檢測。這個面版牽扯到很多記憶體相關的術語，很多我也不是很熟悉，如果你想要深入的了解這個主題，我強烈建議大家可以在看完這個幾天的文章後，再到官方[文件](https://developers.google.com/web/tools/chrome-devtools/memory-problems/) 把記憶體這個區塊看完，如果你只是想要了解開發者工具如何檢測網站的記憶體使用狀況，那讀完這幾天的文章後，我相信你會有個基本的了解。

接下來這幾天我們的進展速度也會比較慢一點，效能面版 (Performance panel) 我們可能是沒有機會詳細介紹了冏，但是希望在討論記憶體檢測時，我們可以至少看一下如何透過它來幫助我們檢測。

## 使用記憶體面版
請先打開 Chrome 開發者工具然後切換到記憶體面版 (Memory panel)，一進來之後你會看到幾個選項：
- Take heap snapshot
- Record allocation profile
- Record allocation timeline

我們今天先從 **Take heap snapshot** 開始介紹，這邊的 **heap snapshot** 官方翻成 **堆快照**，我們今天及接下來幾天使用的範例都是官方文件給的範例，為了方便大家操作，我把這幾個範例都放在 Codepen.io 上，今天使用的範例是[這個](https://codepen.io/konekoya/pen/vpyqby?editors=1010)

在開始之前，我們先來看一下我們這個範例在做什麼：
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
