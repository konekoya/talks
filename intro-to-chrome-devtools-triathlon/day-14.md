
# 行動裝置工具欄
因著現在行動裝置的流行，還有響應式網頁設計 (Responsive Web Design, RWD) 在這幾年成為設計網站流程中重要的一環，Chrome 開發者工具也加入了一個很方便的工具，讓開發者可以很方便的來測試行動裝置，而這工具就是行動裝置工具欄 (Device toolbar)。今天我們就一起來看看如何用這工具來測試響應式網頁吧！

> 我們在簡介行動裝置工具欄的時候就有[提到](https://github.com/konekoya/talks/blob/master/intro-to-chrome-devtools-triathlon/day-5.md#%E8%A1%8C%E5%8B%95%E8%A3%9D%E7%BD%AE%E5%B7%A5%E5%85%B7%E6%AC%84-device-toolbar)，這個工具不能取代使用真實的行動裝置來測試你的網站，因為它仍然有許多限制 (在[官網文件](https://developers.google.com/web/tools/chrome-devtools/device-mode/emulate-mobile-viewports)的 Limitations 有提到)。

## 使用行動裝置工具欄
你可以透過開發者工具左上方的小圖示![打開工具擷圖](https://www.dropbox.com/s/yye3ro96804phdc/device-toolbar.jpg?raw=1)來打開它。或是使用快捷鍵 (Mac 用 Cmd+Shift+M 或是 Windows 用 Ctrl+Shift+M) 
在打開後，首先你會發現你的畫面變小，因為它已經進入預設的行動裝置裡的模式。然後你的滑鼠鼠標 (Cursor) 會變成一個圓點，這是它模擬觸控的方式。
![行動裝置工具欄畫面擷圖](https://www.dropbox.com/s/p2ombturlkih0ox/device-mode.jpg?raw=1)  
**圖 1**: 行動裝置工具欄

這邊值得一提的是，這個模擬模式也包含模擬 User Agent String (UA string)，而這個 UA strting 可以讓網站知道你是用什麼裝置來瀏覽它的頁面，所以像是一些有網站它有另外設計並提供行動裝置使用的子網域，當我們用這個模擬器來查看它們的網頁時，它就會把我們導到行動裝置的子網域去。我們可以用 Yahoo! 的頁面來測試，當你打開行動裝置工具欄後，在你的網址列輸入 https://tw.yahoo.com/ ，它就會把你的頁面導到 https://tw.mobi.yahoo.com/ 而不是一般當我們用桌上型電腦瀏覽器去瀏覽他們的網頁時，直接連到 https://tw.yahoo.com/ 


## 模擬不同裝置
- 切換裝置：當行動裝置工具欄打開後，它會有預設的模擬裝置，你可在左上方的下拉選單中切換。當你切換時，模擬裝置的尺寸、解析度(DPI)還有 User Agent string 等屬性也會跟著一起做切換。這些你也可以自訂某個特定尺寸或是新增其他裝置。除了可以模擬不同的行動裝置外，它也提供了一個 Response mode，這個模式基本上就是讓你的頁面像行動裝置一樣，但是寬度是可以自由調整的(這個選項打開後，畫面的右邊、下面都會多了一個可以左右拖拉的 Bar ，你可以透過它來改變螢幕尺寸)，不用跟任何裝置綁在一起。  
  ![切換裝置擷圖](https://www.dropbox.com/s/kikcuj6v8f5axs5/device-dropdown.jpg?raw=1)  
  **圖 2**: 切換裝置下拉選單，我正在模擬的裝置是 Galaxy S5  
  ![Responsive mode 擷圖](https://www.dropbox.com/s/4s6brzkdwkhu33p/responsive-mode.jpg?raw=1)  
  **圖 3**: 在Responsive 模式下可以自由的調整裝置尺寸，方便做 RWD 測試
  
- 裝置寬高：在裝置下拉選單的右邊有目前選用裝置的寬及高度，如果你是使用 Responsive mode, 它的寬及高可以自由輸入做調整  

- 放大及縮小百分比：百分比下拉選單可以用來放大及縮小目前的螢幕，我通常都使用預設值，不會做調整。  
  ![調整螢幕縮放百分比擷圖](https://www.dropbox.com/s/t8z7q5hwbkdtdqu/zoom.jpg?raw=1)  
  **圖 4**: 調整螢幕縮放百分比
- 旋轉螢幕：使用右上角的旋轉選項小圖示![旋轉螢幕圖示擷圖](https://www.dropbox.com/s/ew1det542uvr3xh/rotate-icon.jpg?raw=1)，你可以切換螢幕成是直立 (Portrait mode) 的瀏覽或是橫式 (Landscape mode) 的，在測試的時候很方便。
  > 如果你使用 Responsive 模式， Rotate 這個選項就不可以使用了
- 網路速度：這裡面有幾個選項
    - online: 正常網路速度
    - Mid-tier mobile: 快速的 3G 網路
    - Low-end mobile: 較慢的 3G 網路
    - offline: 沒有網路連結

我自己在測試時其實比較常用的是 Resposive mode 這個模式，
## 更多選項
在行動裝置工具欄右方有一個三個小點的更多選項，裡面有一些選項是我們可以使用的，我簡單的介紹一下：
- Show device frame: 顯示裝置的外框，不是每個裝置都有，加上去後看起來比較像真的一點。
- Show media queries: 顯示
- Show rulers: 加上尺規，加上去後我覺得很干擾，所以我很少用XD
- Add device pixel ratio: 顯示裝置的 DPI
- Add device type: 加上去後，可以在 Responsive 模式下選用一些不同的模式
- Capture screenshot: 螢幕擷圖(可視範圍)
- Capture full size screenshot: 螢幕擷圖(完整頁面)
- Resets to defaults: 把行動裝置工具欄重設回初始值


## 小結
今天我們一起討論了行動裝置工具欄，這個工具讓我們在做響應式網頁設計測試的時候更為方便，我常常在開發時，就使用這個工具來測試基本的 Media queries 的功能，確定頁面都不會有破圖或是跑掉的問題，然後再使用真的裝置來做測試。因為有時要找到真的裝置來測很困難 (到處借別人手機XD) 所以這不失為一個方便的測試工具，但是我建議幾個重點裝置可以測的話還是用真實的裝置來測，像是 iPhone 及 iPad (都很好借XXXD) ，然後再借個幾支當下比較多人用的 Andriod 手機來測應該就可以了，再進一步的話，可以試試看第三方的服務，像是 [BrowserStack](https://www.browserstack.com/) 來做測試。今天的介紹就到這裡了，希望大家都有收獲，明天我們要一起來看應用面版 (Application panel)
