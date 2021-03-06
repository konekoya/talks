# 原始碼面版 - 在中斷點間移動及觀察變數
到目前為止，我們已經知道怎麼在開發工具裡設置中斷點，也一起討論了兩種設置中斷點的方法跟它們的差異。今天我們要介紹更多除錯的小技巧，準備好了嗎？

## 使用 JS 除錯控制台
在開始之前，請打開官方的 [Demo](https://googlechrome.github.io/devtools-samples/debug-js/get-started) 網頁，然後插入多個中斷點 (沒錯，中斷點是可以有很多個的)，行號分別是 `29`, `32`，然後一樣在畫面上的文字輸入框 **Number 1** 跟 **Number 2** 輸入任意的數字後，按下 **Add Number 1 and Number 2** 這個按鈕。這時候你的程式就會停在中斷點，程式第 `29` 行的位置。如下圖：  
![中斷點29擷圖](https://www.dropbox.com/s/ttilbn6tlytg8wy/breakpoint-1.jpg?raw=1)  
**圖 1**: 中斷點停在程式的第 `29` 行  

> 如果忘了怎麼設置中斷點，請參考原始碼面版 - 使用中斷點 1 裡的 "設定一個中斷點在原始碼中" 的步驟

JS 除錯控制台位在原始碼面版的右邊，這一整排的功能第一次看到的時候我真的不知道該怎麼去用，看起來超級複雜的XD，不過其實實際了解後，它並沒有想像中的複雜而且是非常方便的。

#### 在中斷點中移動
這幾天如果你有跟著我一起設置中斷點，你會發現當中斷點作動中時，在畫面上會有一個 **Paused in debugger** 的工具欄。如下圖：    
![Paused in debugger擷圖](https://www.dropbox.com/s/6jhiddztcwqfuzx/pause.jpg?raw=1)  
**圖 2**: Paused in debugger

這是讓我們可以在多個中斷點中往前移動的方式，當你按下那個像播放的圖示 (繼續執行 Resume script execution) 的時候，中斷點就會往前執行，如果前面的程式裡還有中斷點的話，它就會停在下一個中斷點，所以以我們的例子，當你按下**繼續執行**時，中斷點就會從 `29` 跳到 `32` 並停在 `32` 行。而在這兩個中斷點間我們得到的變數資料也都會改變，就像真的在執行程式一樣。

![Resume script execution擷圖](https://www.dropbox.com/s/ukiadfzo68b7j9g/breakpoint-32.jpg?raw=1)  
**圖 3**: Resume script execution 

> 在你真的在除錯時，你會發現有時候你設的中斷點位置並不是問題所在，也就是說臭蟲不在這，所以常常我會設很多個中斷點，然後使用**繼續執行**在當中移動，直到找到問題點為止。

除了我們剛剛操作的繼續執行這個動作，在**繼續執行**圖示旁邊還有一個 Step over next function call ，這個功能讓你可以跳到下一個方法。
而這兩個功能其實都可以在 JS 除錯控制台找到。並且在 JS 控制台裡還提供了更多在中斷點中移動的方法。

我們在下面一起說明：

- 移動到下個方法呼叫 Step over next function call ![移動到下一個方法呼叫擷圖](https://www.dropbox.com/s/ukqq295rc0z1zp9/step-next.jpg?raw=1) : 讓你移動到下一個方法呼叫，但是不進到方法裡面。在我們的例子中，我們的中斷點會先停在 `29`，當你使用這個功能，它會向下移動到 `30` 行。

- 進入到下一個方法呼叫裡 Step into next function call ![進入到下一個方法呼叫裡擷圖](https://www.dropbox.com/s/wrl9upc0t0xlmfi/step-into.jpg?raw=1) : 進到下一個方法呼叫裡。在我們這個例子裡，你可以在中斷點停在第 `29` 行後，再點選這個功能，這樣程式就會進入 `getNumber` 方法。

- 跳出目前的方法呼叫 Step out of current function ![跳出目前的方法呼叫擷圖](https://www.dropbox.com/s/mkjwhe9edm1xkfj/step-out.jpg?raw=1) :  跳出目前的方法，如果我們用前一個功能進入到一個方法呼叫裡，你想要跳出來，你就可以使用這個選項來離開目前所在的方法。

- 打開及關閉所有中斷點 Deactivate (Activate) breakpoints ![打開及關閉所有中斷點擷圖](https://www.dropbox.com/s/9salbbswi3hx5mh/toggle-pause.jpg?raw=1) : 有時候中斷點太多了，你可能在執行完前面幾個中斷點後，後面的不想要繼續執行。或是說，你想暫時停止所有中斷點的執行，你就可以用這個工具來做開關。

- 在例外時中斷 Pause on exceptions ![在例外時中斷擷圖](https://www.dropbox.com/s/1jhwvbapri3c85i/exception.jpg?raw=1) : 當這個功能打開時，只要你的程式裡有任何例外，它都會觸發中斷點。這個我功能我很少用，因為很多例外的錯誤是來自第三方的程式。但有時候找不到臭蟲的時候我會用它來試著找看看。

#### 觀察特定變數 (Watch)
如果你想觀察某個特定變數的值改變，這個功能就會很方便。現在在 `35` 再加上一個中斷點，然後重覆我們之前的步驟讓中斷點運作，你的畫面應該會像這樣：  
![觀察特定變數擷圖](https://www.dropbox.com/s/m43ini7lc09w2p3/watch.jpg?raw=1)  
**圖 4**: 觀察特定變數   

在JS 除錯控制台裡的觀察 Watch 功能旁有個 `+` 小圖示，點下去並新增一個變數 `sum`，然後使用**繼續執行**來跳到下一個中斷點，直到完成所有中斷點的執行。有注意到 `sum` 這個變數的變化嗎，當我們在程式行號 `35` 的時候，它的值是 `<not available>` 因為它不存在 `getNumber1` 方法裡，當我們往下執行來到 `29` 行時，它變成了 `undefined`，因為它已經被初始化了，但是還沒有給值。再往下執行一直到 `32` 行時，你會發現它有值了。

你在這個觀察功能裡可以新增很多個變數，然後觀察它們的變化，在除錯時，這個是很方便的一個功能。

![觀察特定變數35擷圖](https://www.dropbox.com/s/pvouwunt2q8o68q/not-avaiable.jpg?raw=1)     
![觀察特定變數29擷圖](https://www.dropbox.com/s/lsnhkd6a45a9a8a/undefined.jpg?raw=1)      
![觀察特定變數32擷圖](https://www.dropbox.com/s/ilc2oycsi3jkvl3/12.jpg?raw=1)      
**圖 5**: 變數 `sum` 在程式 `35`, `29` 及 `32` 間的數值變化



## 小結
今天我們很快一起看過怎麼在中斷點中移動還有觀察特定變數的功能。在中斷點間移動的功能其實有時候不是這麼直覺，甚至有時候你的移動會跳到第三方的程式裡面，所以我自己在除錯時，比較常用的還是多設幾個中斷點，然後用**繼續執行**在當中往前移動，並且觀察當中變數的變化，通當這樣就可以找到大部份的問題了。好，雖然我們進度很慢，我覺得應該30天沒辦法講完了XXXD，但是我還是想把除錯這一塊講清楚一點，明天我們會把 JS 除錯控制台的功能講完，然後再來看我們如何跟控制台面版結合除錯。
