# 開發者工具面版簡介 2 - 原始碼、安全性、應用及審查面版

今天我們會再簡單的介紹幾個面版：原始碼、安全性、應用還有審查。好，廢話不多說，就讓我們開始吧！

## 原始碼面版 Sources panel

![原始碼面版擷圖](https://www.dropbox.com/s/p2mqy6yrs42p2aa/souces.jpg?raw=1)

這個面版是在進行 JS 除錯時最常用到的面版之一，以前我們除錯時是用 `console` ，並且在控制台面版檢查輸出的值。但是如果我們使用功能更強大的 `debugger` 時，程式的中斷點 (Breakpoint) 就會顯示在原始碼面版中。除此之外，你在面版的左邊樹狀結構中可以看到整個頁面所用到的原始碼，像是 JS 或是 CSS 等等。在面版的右邊會有一些搭配中斷點可以使用的功能，像是讓你可以追蹤某個變數的狀態，還有目前程式的呼叫堆疊 (Callstack) 等等。另外一個重要的功能就是當中斷點設置後，你還可以使用 step through debugging, 像是走進某個方法裡或是跳過等可以讓你更方便除錯的功能。這些我們在後續的篇幅會再詳細的介紹。

## 安全性面版 Security panel

![安全性面版擷圖](https://www.dropbox.com/s/fnti3as4n84tyx4/security.jpg?raw=1)


這個面版算是一個很簡單的面版，它可以讓你知道這個網站是否安全，而這邊的安全指的是
這個網站是否有使用 [HTTPS](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%AE%89%E5%85%A8%E5%8D%8F%E8%AE%AE), 如果這個網站有使用 HTTPS 並且是有效的，那你就可以看到：這是一個安全的頁面 ( 有效的 HTTPS) "This page is secure(valid HTTPS)"，然後在下面的有效憑證 (Validcertificate) 裡看這個網站所用的[憑證發行機構](https://zh.wikipedia.org/wiki/%E6%95%B0%E5%AD%97%E8%AF%81%E4%B9%A6%E8%AE%A4%E8%AF%81%E6%9C%BA%E6%9E%84)的及憑證的類型。如果要看更詳細的內容就可以點查看憑證 (View certificate)，這個面版的主要功能就是這樣，因為這個面版實在太簡單的，我們接下來就不會再花時間介紹它。

![查看憑證頁面擷圖](https://www.dropbox.com/s/9bz3nlpxr3ap2yj/security-detail.jpg?raw=1)

> 查看憑證頁面，這是 IT 邦幫忙的憑證 


## 應用面版 Application panel

![應用面版擷圖](https://www.dropbox.com/s/9958867zyaxayva/application.jpg?raw=1)


應用面版讓你可以查看及編輯及清除在前端應用的儲存方式及快取，像是：LocalStorage,sessionStorage, IndexedDB 及 cookies 等。在左邊 sidebar 中它也提供一個查看靜態資源的地方叫做 Frames ( 在網路面版或是原始碼也都有存取這些靜態資源的位置 )，最後它也提供一個除錯漸進式網頁應用程式 (progressive web apps, PWA) 的功能。

## 審查面版 Audits panel

![審查面版擷圖](https://www.dropbox.com/s/ptgu7v1qkr5z1vu/audits.jpg?raw=0)


審查面版做的事很有趣，它其實是有點像 Google 的[PageSpeed Insigts](https://developers.google.com/speed/pagespeed/insights/?hl=zh-tw)
的功能，它會讓你知道你的網頁是不是有效能上的問題，有哪些最佳實踐 (Best practices) 是你可以做的，並告訴你實作的方法。算是一個網頁健檢的地方吧 XD

## 小結

今天我們很快的帶過了幾個面版，這些面版都是很重要的主要面版之一，除了安全性面版之外，其他的幾個面版我們在後面都會再花時間更進一步的說明如何來使用。
