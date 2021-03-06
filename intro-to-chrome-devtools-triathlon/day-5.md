# 開發者工具面版簡介 3 - 記憶體面版、行動裝置工具欄及其他工具

到目前為止我們已經看過幾個主要的面版，今天要介紹剩下的一個面版：記憶體面版。但是除了這些面版外，其實 Chrome 開發者工具裡還有提供一些方便的工具來協助工程師們開發及除錯。今天我也會花一點時間來簡單介紹，然而一些比較冷門或是我沒用過的工具就不會介紹了。

## 記憶體面版 Memory panel
![記憶體面版擷圖](https://www.dropbox.com/s/6vid6tudmllnnr2/memory.jpg?raw=1)

這個面版做的事就像這個面版的名稱一樣，讓你來檢查及修正頁面記憶體問題，它可以在任一個頁面產生一個快照，而這個快照 (Heap snapshot) 可以讓你知道當前這個頁面的記憶體使用狀態，而通常在這邊要注意的就是這個頁面是不是有記憶體洩露 (Memory leak) 的問題。我們在接下來的篇幅中會再來介紹這個面版。

## 行動裝置工具欄 Device toolbar
![記憶體面版擷圖](https://www.dropbox.com/s/4ufm3c0pkhdbq02/device-toolbar.jpg?raw=1)

因為這幾年行動裝置的快速增加，很多使用者不再是使用傳統的桌上行電腦來瀏覽網頁，甚至很多使用者大部份時間是只用行動裝置來瀏覽網頁的。所以測試自己的網站是否可以正常的在行動裝置上顯示就是一件很重要的事了。而 Chrome 開發者工具提供的這一個工具就是讓你可以模擬特定的行動裝置，在上面開發及除錯。你可以模擬某個特定裝置的螢幕尺寸，是直立 (Portrait mode) 的瀏覽或是橫式 (Landscape mode)，然後它也會把滑鼠指標轉換成觸控 ( 因為在行動裝置上，是沒有像 element:hover 這類的效果 )，你也可以模擬網路的速度像是 3G 或是 4G 等等方便的功能。但要這裡要注意的是，這只是 " 模擬 " 並不是真的使用這個行動裝置來瀏覽你的頁面，所以在你的網站上線前最好還是使用真實的裝置來測試，我以前就曾遇過使用模擬的方式來測沒有問題的功能，在真的裝置來使用時這個功能卻是有問題的情況。雖然說這個模擬有它的方便性 ( 你不可能有辦法把市面上所有的裝置都買來測一遍吧 …) 及參考價值，但是使用真實的裝置來測才有可能會有百分之百的準確度。

## 其他工具
其他的工具沒有在預設的面版當中，你可以在開發者工具的右上角的三點小點圖示上 ![更多選項擷圖](https://www.dropbox.com/s/4hgosdq1e86gp0f/three-dots.jpg?raw=1) 用滑鼠左鍵點擊一下打開下拉選單，然後再打開 More tools ，我們要介紹的這邊工具就會在這選單裡

![下拉選單擷圖](https://www.dropbox.com/s/dsnpsqxaeo6nm8j/more-options-dropdown.jpg?raw=1)
> 這一個選單也可以在控制台抽屜 (Console drawer) 左上角找到，並且打開一樣的選單

* 動畫 Animation: 你可以查看及除錯你的頁面動畫，這個工具配合樣式控制版 (Styles pane) 一起使用就很方便，你可以看到你寫的動畫樣式及它執行的方式。
![動畫工具擷圖](https://www.dropbox.com/s/f3chrbsciekpgjg/animation.jpg?raw=1)


* 覆蓋率 Coverage: 這是一個才剛剛加入 Chrome 的新功能 ( 在 Chrome 59 加入 )，你可以透過這個功能看到在這個頁面中，有那邊 CSS 跟 JS 是沒有使用到的，算是一個很有趣的功能。
![覆蓋率工具擷圖](https://www.dropbox.com/s/93rylr0rezdaiai/coverage.jpg?raw=1)


* 渲染 Rendering: 這個工具讓你可以檢查目前頁面在進行一些操作時的繪制時間 (Paint time)，像是在畫面捲動時或是一些 UI 操作像是滑鼠事件或 CSS 動畫，這些操作產生的重新繪制都會讓使用者的體驗變差，所以使用這個工具可以檢測那些頁面上的元素正在大量重新繪制，讓頁面顯示速度變差。
![渲染工具擷圖](https://www.dropbox.com/s/cruz8bhmxxakelc/rendering.jpg?raw=1)

![Overlay擷圖](https://www.dropbox.com/s/c5qceg3t3j665xz/rendering-overlay.jpg?raw=1)
> 開發者工具會在頁面上動態顯示目前頁面渲染所使用的資源及其他狀態

## 小結

我們花了三天的時間很快速的把所有面版走過一遍，讓大家對 Chrome 開發者工具有一個基本的概念，接下來我們要開始針對各個面版做詳細的介紹，但在那之前，我們先簡單的介紹一下開發者工具的一些常用設定。
