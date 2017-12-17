
# 原始碼面版 - 找到那個 Bug
今天我們要把 **JS 除錯控制台** 裡的功能講完，然後再介紹在中斷點作用中的時候，我們如何使用**控制台 (Console)** 來快速除錯。

## 使用 JS 除錯控制台
在開始之前，請打開官方的 [Demo](https://googlechrome.github.io/devtools-samples/debug-js/get-started) 網頁，然後打開開發者工具並切換到 **原始碼面版(Sources panel)** 並打開 **get-started.js** 然後在程式碼的行號 `29`, `32` 插入中斷點，再移動到畫面上的文字輸入框 **Number 1** 跟 **Number 2** 輸入任意的數字後，按下 **Add Number 1 and Number 2** 這個按鈕。這時候你的程式就會停在中斷點，程式第 `29` 行的位置。如下圖：

![中斷點擷圖]()

- 呼叫堆疊 Call Stack: 當中斷點作用中的時候，這邊會顯示出接下來要呼叫的方法列表。
