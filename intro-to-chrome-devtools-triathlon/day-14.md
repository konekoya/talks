
# 行動裝置工具欄
因著現在行動裝置的流行，還有響應式網頁設計 (Responsive Web Design, RWD) 在這幾年成為設計網站流程中重要的一環，Chrome 開發者工具也加入了一個很方便的工具，讓開發者可以很方便的來測試行動裝置，而這工具就是行動裝置工具欄 (Device toolbar)。今天我們就一起來看看如何用這工具來測試響應式網頁吧！

> 我們在簡介行動裝置工具欄的時候就有[提到](https://github.com/konekoya/talks/blob/master/intro-to-chrome-devtools-triathlon/day-5.md#%E8%A1%8C%E5%8B%95%E8%A3%9D%E7%BD%AE%E5%B7%A5%E5%85%B7%E6%AC%84-device-toolbar)，這個工具不能取代使用真實的行動裝置來測試你的網站，因為它仍然有許多限制 (在[官網文件](https://developers.google.com/web/tools/chrome-devtools/device-mode/emulate-mobile-viewports)的 Limitations 有提到)。

## 使用行動裝置工具欄
你可以透過開發者工具左上方的小圖示來打開它。或是使用快捷鍵 (Mac 用 Cmd+Shift+M 或是 Windows 用 Ctrl+Shift+M) 
在打開後，首先你會發現你的畫面變小，因為它已經進入預設的行動裝置裡的模式。然後你的滑鼠鼠標 (Cursor) 會變成一個圓點，這是它模擬觸控的方式。
![畫面擷圖]

這邊值得一提的是，這個模擬模式也包含模擬 User Agent String (UA string)，而這個 UA strting 可以讓網站知道你是用什麼裝置來瀏覽它的頁面，所以像是一些有網站它有另外設計並提供行動裝置使用的子網域，當我們用這個模擬器來查看它們的網頁時，它就會把我們導到行動裝置的子網域去。我們可以用 Yahoo! 的頁面來測試，當你打開行動裝置工具欄後，在你的網址列輸入 https://www.yahoo.com.tw ，它就會把你的頁面導到 https://tw.mobi.yahoo.com/ ，很奇妙吧XD
