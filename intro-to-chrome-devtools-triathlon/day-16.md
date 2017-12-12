# 原始碼面版
今天我們要開始來一起討論如何使用原始碼面版 (Sources panel) 來除錯你的網頁。在開發者工具中，我最常用的面版就是元素面版跟原始碼面版，每當我在進行開發的時候，我的開發者工具是一直都開著的，不是在元素面版，就是會在原始碼面版。可見這兩個面版的重要性，我相信在我們一起看完原始碼面版之後，原始碼面版也會成為你每天開發工作中不可缺少的工具。

## 原始碼面版介面簡介
原始碼面版主要由三個大區塊組成：
- 檔案瀏覽控制台 (File Navigator pane): 頁面上所有的資源列表
- 程式編輯控制台 (Code Editor): 當你從檔案瀏覽控制台中選擇檔案後，檔案的原始碼就會出現在這裡
- JS 除錯控制台 (JavaScript debugging pane): 這裡提供了很多除錯 JS 的工具，我們後面會介紹幾個比較常用的

![原始碼面版簡介擷圖]  
**圖1**：原始碼面版由這三個主要的控制台組成

## 使用中斷點 (Breakpoints)
會不會使用中斷點是一個很重要的技巧，當你知道怎麼使用中斷點後，要找到程式中的臭蟲就相對簡單很多。我們今天要使用來除錯的範例是官方文件裡提供的一個 [Demo 網頁](https://googlechrome.github.io/devtools-samples/debug-js/get-started)，我本來是想要一樣用 IT邦的網頁來做介紹，但是怕這樣原始碼內容太多而且複雜，並且網頁有更新的可能，所以最後決定就用官方的文件 Demo

### 設定一個中斷點
在 JS 中，要設定一個中斷點，可以使用 `debugger` 這個關鍵字 (Statement)，如下：
```js
const name = 'Joshua';

debugger; // 在 runtime 中，當程式執行到這裡時，就會停住
console.log(`Hey ${name}`);

```

使用中斷點的時候要注意幾件事：
首先，你的程式需要被**執行到**，不然中斷點並不會被執行，所以下面這段程式的中斷點是不會被觸發的。

```js
const greet = name => {
  debugger
  console.log(`Hey ${name}`);
}

console.log('App is ready!');

```

有看出來為什麼嗎？因為 `greet` 方法沒有被執行，所以 `debugger` 自然沒有被觸發，所以假設我們有 `if` 判斷式：
```js
const isReady = true;
const name = 'Joshua';

if (isReady) {
  console.log(`Hey ${name}`);
} else {
  debugger;
  console.log(`Oops, I'm not ready yet!`);
}

console.log('App is ready!');
```

上面這一段程式一樣不會觸發 `debugger`，所以我們可以清楚的知道，你的 `debugger` 要放在可以被觸發的位置。

好，除了要注意這件事之外，在使用中斷點時，你的開發者工具一定要是開著，不然瀏覽器是不會有任何動作的。

### 設定一個中斷點在原始碼中
我們剛剛提到了如何設定一個中斷點，並且知道中斷點是需要被**執行**並在開發者工具打開著時，才會作動。接下來我們就用官方提供的文件來試試設定中斷點。我需要幾個步驟來完成這個中斷點的設置：

1. 請先連到官方的 [Demo 網頁](https://googlechrome.github.io/devtools-samples/debug-js/get-started)
2. 打開開發者工具並切換到原始碼面版 (Sources)
3. 在左邊的檔案瀏覽控制台中找到一個叫做 **get-started.js** 的檔案。它會藏在 devtools/samples/debug-js 下面，你可以展開上面幾層的結構後找到它。這邊你也可以透過檔案瀏覽控制台的打開檔案來快速搜尋來找到你想要找的檔案：用滑鼠左鍵點一下檔案瀏覽控制台右上方的三個小點圖示，在下拉選單中選擇 Open file ，這時候你應該會看到一個快速搜尋的視窗，在裡面輸入你想要打開的檔案名稱就可以了。也可以用快速鍵打開 (Mac Cmd + P, Windows Ctrl + P)  
    ![快速搜尋視窗擷圖]  
    **圖2**：快速搜尋視窗
