# 控制台面版 1
![控制台擷圖]()

今天我們要一起來討論的 Chrome 開發者工具的控制台面版 (Console panel)，這個面版我們在前面有很[簡單的介紹過](https://github.com/konekoya/talks/blob/master/intro-to-chrome-devtools-triathlon/day-3.md#%E6%8E%A7%E5%88%B6%E5%8F%B0%E9%9D%A2%E7%89%88-console-panel)，其實它就像是一個讀取-求值-輸出循環 (Read-Eval-Print Loop, REPL)，你可以在控制台裡面輸入 JavaScript 的指令，它就會執行並把內容印出來到控制台中。因為這一次的鐵人賽，我開始讀了一些官方的文件，發現控制台面版其實是很複雜的 (真的！相信我XD)，但是我用過的功能只有一小部份，所以我會針對我比較有了解的部份做介紹，剩下的，如果有興趣的朋友，可以到[官方文件](https://developers.google.com/web/tools/chrome-devtools/console/)去讀，我相信是可以挖到很多寶的。

## 使用控制台
控制台使用的方法有兩種，第一種是在打開開發者工具 (參考之前提到的[快捷鍵](https://developers.google.com/web/tools/chrome-devtools/console/)) 後，直接切換到控制台面版。另一種方法則是在任何面版中打開成為一個抽屜 (Drawer)，這種作法是我比較常使用的，並且我會搭配元素 (Elements panel) 跟原始碼(Source panel) 面版一起使用。跟元素面版一起使用的方法我晚點會說明，與原始碼面版搭配則是要拿來除錯，這一部份我們就留到等介紹原始碼面版時再一併討論。

![兩種方法的擷圖]()

## 讀取-求值-輸出循環
這裡簡單的介紹如何使用這個面版來做讀取-求值-輸出循環。在打開面版之後如果你的面版裡有其它的 Log，你可以用左上角的小圖示![清除擷圖]()先把它先清除，清除後我們就可以開始來寫一點簡單的 JavaScript。
- 你可以用這個面版來做數值的運算，就像是在 JavaScript 裡一樣：在面版中輸入 `5+5` 你應該會得到 `10` ，結果應該會出現在輸入的程式正下法。題外話一下，我常常用控制台來做我的小算盤XD
- 你可以宣告變數，重新指定值 (assign)：
```javascript
// 宣告變算數
var x = 10;

// 重新指定值
x = function() {
  console.log('Hello world from console!');
}

x() // 會印出 Hello world from console!
```

> 當你執行上面這一段程式後，除了會得到 `Hello world from console!` 在控制台面版中，應該還會得到一個 `undefined`，這是因為當呼叫一個方法時，控制台面版也會把這個方法的傳回值 (return) 回傳回來。而因為我們定義的方法 `x` 並沒傳回任何值，所以回傳的預設值就是 `undefined`
