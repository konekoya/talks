# 開發者工具面版簡介 1 - 元素、控制台、網路及效能面版

接下來的幾天我們會很快的把所有的 Chrome 開發者工具的面版走過一遍，並且有一點簡單的介紹，讓大家對這些面版有些基本的認識，之後我們會針對幾個我認為比較重要的面版做詳細的介紹。

> 關於翻譯：\
> 在我們的文章中，Panel 我把他翻成 " 面版 "； Pane 則是翻成 " 控制版 ""，然而在有
> 些中文文件的翻譯是翻成 " 窗格 "。

## 元素面版 Elements panel

![元素面版擷圖](https://www.dropbox.com/s/i135yjo4qex76vq/element.jpg?raw=1)

元素面版是一個非常重要的面版，也是 Chrome 開發者工具很早期的時候就加入的面版之一。通常在你一打開開發者工具之後 ( 在 Windows 可以用 F12 或 Control+Shift+I ，如果是在 Mac 可以用 Command+Option+I 來打開 )，元素面版讓你可以：

* 查看 (inspect) 及動態編輯 (Live-edit) 文件物件模型 (DOM)，所以在編輯後是可以直接看到效果的，就像所見即所得編輯器 (What You See Is What You Get)
* 查看每個元素的樣式並動態編輯，它有一個自己的控制版 (pane)，叫做樣式控制版 (Styles pane)
* 查看及動態編輯所選擇的元素的計算後的區塊模型 (Box model)，它也有一個自己的控制版，叫做計算控制版 (Computed pane)

## 控制台面版 Console panel

![控制台面版擷圖](https://www.dropbox.com/s/q6k6wsznmkrbswg/console.jpg?raw=1)

控制台面版是一個有點像是
[REPL](https://zh.wikipedia.org/wiki/%E8%AF%BB%E5%8F%96%EF%B9%A3%E6%B1%82%E5%80%BC%EF%B9%A3%E8%BE%93%E5%87%BA%E5%BE%AA%E7%8E%AF)
的一個面版，你可以在這邊使用絕大部份的 JavaScript 語法，並且可以立即看到執行後的效果。除此之外它也可以輸出程式中 `console.log` 的內容，是除錯的好幫手，也可以搭配元素面版及原始碼面版 (Sources panel) 一起使用。

## 網路面版 Network panel

![網路面版擷圖](https://www.dropbox.com/s/duu7i0du3saade7/network.jpg?raw=1)

網路面版可以讓你查看所有透過 HTTP 上傳及下載的要求，也可以看到頁面整體的載入所花的時間，甚至詳細的知道每一個資源載入的時間點。所以透過網路面版你可以輕易解你的頁面與伺服器的互動狀況。

## 效能面版 Performance panel

![效能面版擷圖](https://www.dropbox.com/s/aj4hkhtmy7r489q/performance.jpg?raw=1)

效能面版之前原本叫做 Timeline，但是在一次的改版中改掉了。這一個面版應該是所有面版中最複雜、功能最多的一個面版。簡單的來說，它是一個可以讓你檢查及了解頁面渲染效能的工具。你可以查看頁面是不是有記憶體洩漏，CUP 的使用狀況，甚至什麼時候有GC(Garbage collection) 它都知道。所以當你想要調校你的網頁效能時，這會是一個很方便的工具。

## 小結

今天我們很簡略的介紹了幾個面版，但其實這每一個面版都可以花上好幾天的時間來討論，在這系列的文章中，我們會特別並且深入了解的會有元素面版、控制台還有網路面版。而效能面版的部份因為我本身的理解有限，所以雖然也會花時間討論，但就會是以目前我比較常用的功能為主。
