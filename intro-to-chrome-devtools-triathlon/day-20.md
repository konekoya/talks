# 網路面版 - 介面簡介
今天要一起來看的是網路面版 (Network panel)，網路面版主是要拿來檢查資源透過 HTTP 傳輸的狀況。當我們的瀏覽器向網頁伺服器發出要求直到伺服器把所有我們頁面所需資源送回來的這一段過程，都可以透過網路面版來做檢查。

## 網路面版介面
網路面版提供了許多功能，算是一個比較複雜的面版，我們會多花幾天的時間詳細介紹

![介面擷圖](https://www.dropbox.com/s/mwli4uxhzi63url/interface.jpg?raw=1)  
**圖 1** : 網路面版由總覽及請求列表組成 

在打開網路面版後，在面版主要分成兩大塊，一塊是上方類似時間軸的區塊叫做總覽 (overview)，然後下面會是網頁與伺服器的 HTTP 請求。如果你的總覽或是下方的 HTTP 請求列表 (Request row) 裡沒有任何內容，請再重新整理一次頁面，因為網路面版的一些 HTTP 請要在我們打開開發者工具前可能就載進來了，有時候它並不會全部都記錄到。

## HTTP 請求列表
> 我們今天用來使 Demo 的網頁是 [IT邦幫忙的首頁](https://ithelp.ithome.com.tw/)

#### 過濾 HTTP 請求
在詳細查看一則請求前，我們需要先學會如何過濾請求。在面版的上方工具列有一個過濾按鈕 ![過濾按鈕](https://www.dropbox.com/s/615f9g9l07ca026/filter-icon.jpg?raw=1) ，如果你的過濾按鈕還沒有打開，請打開它。在打開之後它會提供幾個不同的過濾選項，讓我們先從 **All** 切換到 **XHR** ，在切換到 **XHR** 後，下方的請列表明顯變少了，在我的頁面上只剩 4 個請求。你現在可以切換到其他的類別看看，如果你想要過濾多個類別，可以按住鍵盤上的 Cmd 鍵 (windows 用 Ctrl) 再用滑鼠來點選你想要過濾的類別，這樣就會一次過濾多個類別。
![過濾下拉選單擷圖](https://www.dropbox.com/s/sekgxe5ypd2mk2n/filter-dropdown.jpg?raw=1)  
**圖 2** : 過濾按鈕按下後打開的下拉選單裡會有不同的過濾選項


除了透過類別來做過濾外，你當然也可以使用過濾選單裡的搜尋來做更精確一點的尋找。還有一點要提醒的事，這些使用的過濾類別會一直作用，也就是說，我現在選擇了 **XHR** 當過濾分類，當你切換網站或是下次再打開網路面版時，它會仍然在 **XHR** ，你就只會看到 **XHR** 相關的請求而看不到其他類別。我自己就發生了很多次找不到特定請求，最後發現是因為忘了把過濾分類切回 **All** 冏

> 開發者工具其實有提供一個小提示：當我們有設定過濾分類時，過濾按鈕會變成紅色的 ![紅色過濾按鈕擷圖](https://www.dropbox.com/s/o65m37d45tujxn5/filter-active.jpg?raw=1)

#### 刪除及停止記錄
網路面版預設會一直記錄所有的 HTTP 請求，你可以透過左上角的記錄按鈕來開關它 ![開啟及停止錄制按鈕擷圖](https://www.dropbox.com/s/7lssofo0n9km39u/record.jpg?raw=1) 。通常我要停止記錄時是因為我想看某個特定的 **XHR** 請求，但是因為頁面還在載入，它還有很多請求在後面，會一直跑進來，這樣會變太多資訊，所以我就會把它關掉，等到檢查完再把它打開。

刪除記錄 ![刪除記錄按鈕擷圖](https://www.dropbox.com/s/7an9wf0oyyra0fn/clear.jpg?raw=1) 也是一個很常用到的功能，假設我的頁面已經載完了，我有一個互動的介面，當使用者點下後會觸發 **XHR** 的動作，產生請求在網路面版中。我就會先把 **XHR** 裡的請求先全部清掉，然後再來測試這個互動介面。這樣的話，我的介面就很乾淨，只會有這個介面所產生的請求，方便做除錯。

#### 調整 HTTP 請求列表資訊
請求列表可以透過面版上方的調整按鈕 ![調整 HTTP 請求列表資訊按鈕擷圖](https://www.dropbox.com/s/j1kxw6r6ggv4heu/request-row-toggle.jpg?raw=1) 來切換大小，較大的請求列表會有較多的資訊，較小的就比較少，如果沒有什麼特定原因的話，我建議就用大的，這樣資訊比較多。

#### 開關總覽
如果你覺得請求列表空間不夠，可以透過面版上方的開關總覽按鈕 ![開啟及關閉總覽按鈕擷圖](https://www.dropbox.com/s/913n3qfiinjgsbb/waterfall.jpg?raw=1)來關閉總覽。


## 小結
今天算是一個熱身，我們簡單的把請求列表看過，接下來我們要在明天介紹如何使用總覽來查看不同資源的載入時間 :)
