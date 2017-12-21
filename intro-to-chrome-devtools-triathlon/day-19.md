
# 原始碼面版 - 找到那個 Bug
今天我們要把 **JS 除錯控制台** 裡的功能講完，然後再介紹在中斷點作用中的時候，我們如何使用**控制台 (Console)** 來快速除錯。

## 使用 JS 除錯控制台
在開始之前，請打開官方的 [Demo](https://googlechrome.github.io/devtools-samples/debug-js/get-started) 網頁，然後打開開發者工具並切換到 **原始碼面版(Sources panel)** 並打開 **get-started.js** 然後在程式碼的行號 `29`, `32` 插入中斷點，再移動到畫面上的文字輸入框 **Number 1** 跟 **Number 2** 輸入任意的數字後，按下 **Add Number 1 and Number 2** 這個按鈕。這時候你的程式就會停在中斷點，程式第 `29` 行的位置。如下圖：

![中斷點擷圖](https://www.dropbox.com/s/cb2v7u8kjnseul2/breakpoint-29.jpg?raw=1)
**圖 1** : 在程式第 `29` 行中斷點

- 呼叫堆疊 Call Stack: 當中斷點作用中的時候，這邊會顯示出接下來要呼叫的方法列表，點選列表中的方法會跳到該方法去。在我們的 Demo 中，我們目前停在程式行號 `29`，這時候的 Call Stack 如下圖：

![呼叫堆疊擷圖](https://www.dropbox.com/s/hr57btxozjpx7y1/call-stack.jpg?raw=1)

- 變數作用域 Scope: 一樣是在中斷點作用中的時候，這邊會列出可用的變數列表分成區域及 (Local) 及 全域 (Global) 變數。所以當我們切換中斷點時，裡面的變數就會跟著變化，特別是區域變數會隨著當前 JavaScript Scope 而不同。目前我們的變數作用域如下圖：

![變數作用域擷圖](https://www.dropbox.com/s/t32l031ujy3ew5x/scope.jpg?raw=1)

- 中斷點 Breakpoints: 這邊列出了我們設的幾個中斷點，然後你可以透過它前面的 checkbox 來開關中斷點

- XHR 中斷點 XHR/fetch Breakpoints: ajax 呼叫中斷點，你可以透過它右上角的加號按鈕來新增中斷點

- DOM 中斷點 DOM Breakpoints: 還記得我們之前在元素面版有提到過的中斷點嗎？你在這邊也可以開關這些中斷點

- 全域事件 Global Listeners: 這邊會有註冊在全域 (window) 下的所有事件列表

![中斷點 XHR DOM 及全域事件擷圖](https://www.dropbox.com/s/i0i5lpzstcdw3dc/breakpoints-xhr-dom-global-listeners.jpg?raw=1)


- 事件中斷點 Event Listener Breakpoints: 這是一個蠻有趣的功能，它提供了很多不同的事件中斷點讓你可以做檢查，像是 `Animation`, `Load` 還有像是常見的滑鼠及鍵盤等事件。你可以在這些事件的 checkbox 上打開啟用這些事件。假設我打開了 Mouse 下的 click 事件，這樣當頁面上有任何 Mouse click 事件發生時，中斷點就會停在這個事件相關的程式中。

![事件中斷點擷圖](https://www.dropbox.com/s/8rxxiqirdqc1r7a/events.jpg?raw=1)


> 當我們在看原始碼時，有時候這些原始已經被 minify 或是 uglify 過了，要除錯或是追蹤程式會很困難。你可以使用原始碼面版左下角的 `{}` 按鈕來展開它

## 與控制台結合使用
當中斷點作用中時，我們也可以使用控制台來協助我們除錯。現在讓我們用 ESC 鍵打開控制台抽屜並讓你的程式中斷並停在行號 `29` (如果你還沒有設置中斷點，請參考開頭提到的中斷點設置方式)，這時候你的畫面應該會像下圖：

![中斷點擷圖](https://www.dropbox.com/s/tbcauqk6148svgx/console.jpg?raw=1)

好，現在我們可以直接在控制中輸入變數名稱：
```js
addend1 // undefined
addend2 // undefined
sum // undefined
this // window
```
結果應該像下圖：
![中斷點擷圖](https://www.dropbox.com/s/lym9kay712nelzh/breakpoint-29-undefined.jpg?raw=1)

很神奇吧！我們現在可以存取目前程式中斷 Scope 裡的變數值，而因為我們目前中斷的位置，我們的變數都是 `undefined`，現在讓我們移動到行動 `32` 的中斷點
然後再下面再輸入這些值，這裡是假設我在文字輸入框分別輸入數字 `1` 及 `2` 

```js
addend1 // "1"
addend2 // "2"
sum // "12"
```
結果應該像下圖：
![中斷點擷圖](https://www.dropbox.com/s/wmxv99psj518ngg/breakpoint-32-bug.jpg?raw=1)

好，你心或許會想說，這樣只是把值顯示出來，我們前面不是提到很多方法可以知道變數的值了嗎？對，沒錯。但是在這裡我們可以直接操作變數並且除錯，還記得我們前面有提到這個 Demo 有個臭蟲嗎？聰明的你應該已經看出來了，我們從文字輸入框得到的數值型別是字串 (string)，所以當它們相加時，會變成文字的串接而不是數值的運算。好，我們知道問題了，而且字串轉數值也很簡單，我們可以直接在控制台裡試著使用我們的解法：

```js
sum = parseInt(addend1) + parseInt(addend2) // 3
```
結果應該像下圖：
![中斷點擷圖](https://www.dropbox.com/s/c2pvk1ofnf5ubvm/fixed.jpg?raw=1)

看起來沒有問題，我們得到正確的數字了。讓我們來修正我們原始碼裡的程式碼
```js
function updateLabel() {
  var addend1 = getNumber1();
  var addend2 = getNumber2();
  var sum = parseInt(addend1) + parseInt(addend2); // 把我們剛剛在控制台裡想到的解法放裡來
  label.textContent = addend1 + ' + ' + addend2 + ' = ' + sum;
}
```

修正後的中斷點應該像下圖：
![修正後的中斷點擷圖](https://www.dropbox.com/s/c2pvk1ofnf5ubvm/fixed.jpg?raw=1)


修改完要記得存檔，然後我們再試著輸入數字來做加總測試，看起來都沒有問題，喔耶！
如果這是我們自己的程式，那在這個階段後或是在剛剛我們在控制台找到問題後，就是把修改完的程式放到我們自己的原始碼中，這樣就完成除錯的過程了。

## 小結
我們今天一起把 **JS 除錯控制台** 裡的功能都看完了，也試著用控制台面版來做除錯。雖然我們解的這個問題很簡單，但是這就是我們一般除錯的流程：
```
設置中斷點來縮小問題範圍 -> 找到問題點 -> 如果可以，在控制台中嘗試解決這個問題 -> 回到我們的原始碼中貼上問題解法 -> 再次測試
```
當然在更複雜的專案中常常要找到臭蟲就要很長的一段時間，解法也沒有像我們今天的例子這麼簡單直覺，但是我相信只要多練習，讓你自己熟悉開發者工具，整個除臭體驗是一定會比從前我們只用 `alert` 或是下一堆 `console.log` 好很多。好，我們今天就講到這裡，明天我們要來講 **網路面版 (Network panel)** ，這是一個除錯 Ajax 時很重要的一個面版，讓我們一起來學習吧！
