# 控制台面版 1 - 與元素面版一起使用
昨天我們簡單的介紹了控制台面版的讀取-求值-輸出循環功能，今天我們要一起要來看它提供的一些方便的 API，以及如何透過這些 API 與元素面版一起使用。

## 常見 API
因為我們今天的介紹的功能大部份跟元素面版有關，所以請直接打開面版，如果你的控制台抽屜沒有打開的話，可以用 ESC 鍵打開。
而我們使用的範例網站是 [GitHub 的首頁](https://github.com/)

#### $_
這個指令讓你可以再一次執行上一次執行過的指令。假設剛剛執行過一個指令
```js
8 + 4 // 12 
```
使用 $_ 後，我們就會再一次得到 12 這個結果。

#### $0 - $4
這個指令讓你可以得到你曾經在元素面版中拜訪過的元素的 DOM，什麼意思呢？就是當你使用滑鼠或是鍵盤在元素面版的 DOM 樹中移動時，開發者工具會記住最接近你的五次操作的元素，而這些 DOM 元素可以透過 $0 - $4 來在控制台中存取，我們來看個例子

在 GitHub 首頁的 DOM 樹中，我們可以先移動到 body 然後移到有一個 class 名稱叫做 footer 的 div，最後到 class 名稱叫做 facebox 的 div 元素。
這時候如果我們用 $0, $1, $3 控制台中，就會得到這幾個 DOM 元素及它下們的子孫元素。

```js
$0 // <div class="facebox" id="facebox" style="display:none;">
$1 // <div class="footer container-lg p-responsive mt-6" role="contentinfo">
$2 // <body class="logged-out env-production page-responsive min-width-0 f4" data-gr-c-s-loaded="true">
```

