# 審查面版
我們在前面有簡單介紹了審查面版(Audits panel)，它可以幫我們檢測我們的網站是不是有遵循最佳實踐 (Best practices)，並提供我們每個問題的解決方式，讓我們的網站更快更穩定。

> 審查面版最近才大改版，加入了 (Progressive Web App (PWA)) 功能，改到我都快不認識了 XXXD

## 開始審查

> 今天的範例網站一樣是使用 [iT邦幫忙的首頁](https://ithelp.ithome.com.tw/)

打開你的 Chrome 開發者工具並切換到審查面版，在這裡我們可以用 **Perform an audit** 來進行頁面的審查，在開始審查前，它會問你要針對哪幾個選項來做審查，我們今天只做 **Performance** 及 **Best practices**，在勾選這兩個項目後，按下 **Run audit** 來進行審查。這個過程要一點時間，要等一下。

![我們今天只做 Performance 及 Best practices 面版擷圖](https://www.dropbox.com/s/g7ho65ptndsazqc/audits.jpg?raw=1)
**圖 1** : 我們今天只做 Performance 及 Best practices 面版

在跑完之後我們會得到一頁報告，在開始看之前，我們先看一下在工具列上的幾個功能
- New audit: 再新增一個審查
- Download report: 下載這個報告，下載後的檔案是一個 `JSON` 檔，下次要看時可以再用審查面版載入
- Clear all: 清除所有報告

中間還有一個下載選單是讓你可以在多份報告中切換

現在就讓我們一起來看這份報告

![Audits 面版產出的報告擷圖](https://www.dropbox.com/s/tlcggxh2k15xz6i/report.jpg?raw=1)
**圖 2** : Audits 面版產出的報告 

#### 效能 Performance
在頁面的上方會有 **Performance** 的分數，在我錄制的這一次審查報告中是 8 分(滿分是 100)，為什麼分數會這麼低…我們一起來看看 (iT邦的開發團隊不要 K 我冏，我不是打分數的人) 

在 **metrics** 裡有螢幕的擷圖它可以配合跟下面的 **First meaningful paint**, **First interactive (beta)** 等頁面載入的時間點一起看，但我們要來看的是更有趣的部份，在 **Opportunities** 裡它提供了幾個可以提升我們頁面載入效能的建議，我們來看其中幾個：

- Reduce render-blocking stylesheets: 這邊它會告訴你哪些 CSS 檔案影響了頁面載入的效能，並告訴你如何來最佳化，後面提供的連結會連到官網文件，在那裡會有更多說明

- Enable text compression: 針對文字類型的請求 (像 JS, CSS 等)，使用壓縮技術來降低傳輸的時間，它後面一樣也提供了官網文件的說明

- Keep server response times low(TTFB): 還記得我們在網路面版裡提到的 Time to First Byte? 這個審查項目就是要你的伺服器在最快的時間點內開始回傳請求的資料

下面還有 **Diagnostics** 裡面有更多頁面效能資訊可以看，裡面有一個有趣的資訊：它期待頁面所有載入的資源大小要小於 1,600 KB 也就是 1.6 MB
最下面是有通過的審查項目，在這一次的審查裡總共有 5 個
 
#### 最佳實踐 (Best practices)
在 **Failed audits** 這裡面就有更多建議做法來最佳化我們的頁面，我們一樣一起來看幾個項目

- Does not use HTTP/2 for all of its resources: 這裡提到頁面上有部份的資源不是透過 HTTP 2 來做傳輸，展開後在下面列表裡會有所有沒有使用 HTTP2 傳輸的請求

- Includes front-end JavaScript libraries with known security vulnerabilities: 這裡列出載進頁面的 JS 資源有的安全性弱點，在我們這個例子裡是 jQuery@1.11.1 ，你可以點選它的連結，它會帶你到弱點分析的網站告訴你這個安全性問題是什麼

- Browser errors were logged to the console: 這邊列出控制台面版裡得到的錯誤 log 訊息，並建議把它處理掉

下面列的是 **Passed Autdits** 是有通過的審查

## 小結
改版後的審查面版威力更強大了，裡面提供的審查項目可以讓我們來調整並最佳化我們開發的網頁，當然有些最佳化的項目我會覺得只要參考就好，如果因著要最佳化某個項目來大改動我們的頁面架構或改寫程式，我覺得都要好好的考慮清楚這樣做是否值得。但一些簡單並且明顯可以做的，像是用 `gzip` 來減少下載資源大小或是避免使用 `document.write()` 來加快載入效能，這些就是我可以不用考慮太多，直接可以執行的。好，審查面版就講到這裡，明天我們一起來看記憶體面版 (Memory panel)
