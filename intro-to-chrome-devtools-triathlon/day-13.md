# 控制台面版 2 - 結合元素面版
昨天我們簡單的介紹了控制台面版的讀取-求值-輸出循環功能，今天我們要一起要來看它提供的一些方便的 API，以及如何透過這些 API 與元素面版一起使用。

## 常見 API
因為我們今天的介紹的功能大部份跟元素面版有關，所以請直接打開面版，如果你的控制台抽屜沒有打開的話，可以用 ESC 鍵打開。
而我們使用的範例網站是 [iT幫邦忙的首頁](https://ithelp.ithome.com.tw/)

#### $_
這個指令讓你可以再一次執行上一次執行過的指令。假設剛剛執行過一個指令
```js
8 + 4 // 12 
```
使用 $_ 後，我們就會再一次得到 12 這個結果，如下圖：

![再執行一次上一次的指令擷圖](https://www.dropbox.com/s/t4rq3p6s6otxskd/redo-the-command.jpg?raw=1)  
**圖 1: $_ 可以再執行一次上一次的指令**

#### $0 - $4
這個指令讓你可以得到你曾經在元素面版中拜訪過的元素的 DOM，什麼意思呢？就是當你使用滑鼠或是鍵盤在元素面版的 DOM 樹中移動時，開發者工具會記住最接近你的五次操作的元素，而這些 DOM 元素可以透過 $0 - $4 來在控制台中存取，我們來看個例子

在 GitHub 首頁的 DOM 樹中，我們可以先移動到 body 然後移到有一個 class 名稱叫做 footer 的 div，最後到 class 名稱叫做 facebox 的 div 元素。
這時候如果我們用 $0, $1, $3 控制台中，就會得到這幾個 DOM 元素及它下們的子孫元素。如果你用滑鼠移動到這元素上，開發者工具會顯示它在頁面的位置，如果你用滑鼠右鍵打開更多動作選單，並選擇 Reveal in Elements panel 它就會帶你回到元素面版裡 DOM 樹中這個被選擇元素的位置。

```js
$0 // <div class="facebox" id="facebox" style="display:none;">
$1 // <div class="footer container-lg p-responsive mt-6" role="contentinfo">
$2 // <body class="logged-out env-production page-responsive min-width-0 f4" data-gr-c-s-loaded="true">
```

#### $(選取器)
如果有用過 jQuery 的朋友，應該對種選擇方式不漠生，但這個 API 跟 jQuery 的 `$()` 是有點差異的。在這裡它背後其實是呼叫 `document.querySelector()` 這個 DOM API ，所以如果我們用 `$('div')` 來選擇頁面上的 div 元素，如果這個頁面上有多個 div 元素，它就只會回傳第一個。下面再舉幾個例子

```js
// 一般的元素
$('body') // <body class="homepage enhanced js" id="home" data-gr-c-s-loaded="true">

// class
$('.main-header') // <header class="main-header block">

// ID
$('#main') // <main id="main" tabindex="-1">
```
#### $$(選取器)
這個與我們剛剛介紹的 `$()` API 很像，只是它背後是呼叫 `document.querySelectorAll()` ，所以它是可以一次選取多個元素的。以剛剛的 `$(div)` 例子，改成 `$$(div)` 我們就會得到所有的 div 元素。我再一起來看一個例子：

```js
var anchors = $$('a'); // 選取頁面上所有的 a 元素
anchors.forEach(a => console.log(a.href)) // 印出所有連結元素的連結

```

#### copy
有時候當你選取了某個元素後，你想要拷貝它就可以用這個指令，並且可以用快捷鍵 (Mac Cmd+V 或 Windows Ctrl+V) 來貼到像是文字編輯器等工具裡面。
```js
// 假設 $0 是 body 元素，你就可以拷貝包含它所有子孫元素的 DOM 樹
copy($0)
```

#### clear
清除所有在控制台中的資訊，這個功能是個方法，跟一般 Linux Terminal 裡的 `clear` 不一樣，是需要呼叫才能使用
```js
clear()
```

## 小結
我們今天介紹了幾個常見及常用的 API，而且這些 API 大部份是可以與元素面版做結合使用的。透過這些 API 你可以更快速的找到你想要操作的 DOM 元素，然後直接在控制台面版中編輯及改變它，要記得你得到的這些元素的操作會直接反應在頁面上。配合我們前幾天介紹的元素面版，你現在已經有完整的元素及樣式操作的工具，在不離開瀏覽器的情況下，你也可以操作及改變頁面上許多介面的畫面及結構。有覺得很強大嗎XD，好，不說廢話了。今天所介紹的這些控制台面版 API 是我自己本身比較常用的，如果你想要了解更多，你可以到[官網的文件](https://developers.google.com/web/tools/chrome-devtools/console/)上去看。接下來我們要一
討論的是行動裝置工具欄，那就明天見啦 :)

