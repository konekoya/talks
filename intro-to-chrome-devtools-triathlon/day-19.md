
# 原始碼面版 - 找到那個 Bug
今天我們要把 **JS 除錯控制台** 裡的功能講完，然後再介紹在中斷點作用中的時候，我們如何使用**控制台 (Console)** 來快速除錯。

## 使用 JS 除錯控制台
在開始之前，請打開官方的 [Demo](https://googlechrome.github.io/devtools-samples/debug-js/get-started) 網頁，然後打開開發者工具並切換到 **原始碼面版(Sources panel)** 並打開 **get-started.js** 然後在程式碼的行號 `29`, `32` 插入中斷點，再移動到畫面上的文字輸入框 **Number 1** 跟 **Number 2** 輸入任意的數字後，按下 **Add Number 1 and Number 2** 這個按鈕。這時候你的程式就會停在中斷點，程式第 `29` 行的位置。如下圖：

![中斷點擷圖]()

- 呼叫堆疊 Call Stack: 當中斷點作用中的時候，這邊會顯示出接下來要呼叫的方法列表，點選列表中的方法會跳到該方法去。在我們的 Demo 中，我們目前停在程式行號 `29`，這時候的 Call Stack 如下圖：

![呼叫堆疊擷圖]()

- 變數作用域 Scope: 一樣是在中斷點作用中的時候，這邊會列出可用的變數列表分成區域及 (Local) 及 全域 (Global) 變數。所以當我們切換中斷點時，裡面的變數就會跟著變化，特別是區域變數會隨著當前 JavaScript Scope 而不同。目前我們的變數作用域如下圖：

![變數作用域擷圖]()

- 中斷點 Breakpoints: 這邊列出了我們設的幾個中斷點，然後你可以透過它前面的 checkbox 來開關中斷點

- XHR 中斷點 XHR/fetch Breakpoints: ajax 呼叫中斷點，你可以透過它右上角的加號按鈕來新增中斷點

- DOM 中斷點 DOM Breakpoints: 還記得我們之前在元素面版有提到過的中斷點嗎？你在這邊也可以開關這些中斷點

- 全域事件 Global Listeners: 這邊會有註冊在全域 (window) 下的所有事件列表

- 


