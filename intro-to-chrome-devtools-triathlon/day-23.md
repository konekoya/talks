# 網路面版 - 了解每個請求
經過這幾天的介紹，我想大家對這個面版已經有一定的認識了，但是我們其實還沒有進到每個 HTTP 請求裡面，去查看這個請求細節，而這就是我們今天要做的。好，就讓我們一起開始吧！

## 進入請求細節
一開始我們一樣先打開 Chrome 開發者工具然後切換到網路面版 (Network)，這時候你的頁面可能沒有完整的 HTTP 請求列表，請重新整理一下你的頁面，你應該就會得到一個完成的 HTTP 請求列表在你網路面版裡面。

> 今天我們用的範例網站一樣是 [iT 邦幫忙的首頁](https://ithelp.ithome.com.tw/)

我選用的 HTTP 請求是 `ithelp.ithome.com.tw` 的 `document` 文件。在用滑鼠左鍵點擊後，它會在請求的右邊打開一個新的頁面顯示請求細節，如下圖：

![請求細節擷圖](https://www.dropbox.com/s/e0t4gt933688jgi/header.jpg?raw=1)
**圖 1** : HTTP 請求的細節頁面

這個頁面裡有幾個頁籤，我們一起來看：

#### 表頭 Headers

> 在表頭裡會有很多資訊是來自 HTTP 協定，很多內容其實我並不了解(光 HTTP 應該就可以寫一個系列文XD)，所以我介紹的會是我知道的，你如果有特別想知道的 HTTP 資訊，可以拿那個資訊的名稱去做搜尋，應該很快就可以找到相關的文件

每個 HTTP 請求裡都會包含這個資訊，在這裡面它又分成了幾個區塊：
- General: 這裡算是一個比較精簡資訊的整理，讓你可以很快的知道這個請求的位置 (Request URL), 請求方式 (Request Method), 這個請求的狀態 (Status Code)

- Response Headers: 這裡面就是伺服器在接收到我們的請求後回傳的表頭，裡面會有快取設定 (Cache-Control), 內容編碼方式 (Content-Encoding), 內容大小(長度) (Content-Length), 內容類別 (Content-Type) 還有是那一種伺服器 (Server)，你可以用 `view source` 來看它的原始資料，我們目前看的這個列表是開發者工具有整理過的

- Request Headers: 這就是這個請求送出的要求訊息，裡面會有接受的類別 (Accpet), 編碼方式 (Accept-Encoding), 語言 (Accept-Language), 位置 (Host) 及使用的瀏覽器 (User-Agent)，跟 Response Headers 一樣，你也透過 `view source` 可以看它的原始資料

如果你的請求有使用到參數，那可能還會有下面的欄位，裡面會有你的請求所帶的請求參數，在除錯的時候常常會需要看這些參數
- Query String Parameters
- Form Data

#### 預覽及回覆 Preview and Response
這兩個頁籤其實有點像，官方文件裡我也沒有找到有什麼不同… 但是 Preview 算是我比較常用的，你可以用它來看回傳的資源內容，像是圖片，它就會直接顯示圖片給你看，如果是像 JSON 類的資料，它會整理成一個類似 tree 的列表給你看

![預覽擷圖](https://www.dropbox.com/s/t8yo6910ff5fjww/preview.jpg?raw=1)
**圖 2** : 預覽及回覆的內容在我們這個例子裡有著一樣的內容

#### Cookies
這邊就是可以看到這個請求的 cookies 資訊

![cookies 擷圖](https://www.dropbox.com/s/veb8ihpeq926tp2/cookies.jpg?raw=1)
**圖 3** : 在這個頁面裡可以看到 cookies 的詳細內容

#### 時間 Timing
這個頁籤就有比較多資訊我們可以一起來看了(這裡使用的 HTTP 請求改為 `simplemde.min.css` 這個檔案，它的資訊比較完整)，有些資訊官方文件也沒有提供，我就沒有列在下面
> Chrome 一次可以同時處理的 HTTP 請求為 6 個，所以一個頁面如果有超過 6 個請求，它就會把這些請求分批處理。而這個限制是在 HTTP/1.0 及 1.1，HTTP2 就沒有這個限制，它可以一次處理所有請求

- Queueing: 在請求開始前，等待的時間 
- Stalled: 跟 Queueing 類似，也是在等待
- DNS Lookup: 在做 DNS Lookup 所需要時間，瀏覽器在轉換請求的 IP 位址
- Waiting (Time to Fisrt Byte : TTFB): 簡單的說，就是瀏覽器開始接收資料的時間
- Content Download: 請求內容下載所花的時間

![Timing 擷圖](https://www.dropbox.com/s/tdmjk4bb3rvxmos/timing.jpg?raw=1)
**圖 4** : Timing 頁面裡可以看到與前面介紹的 Waterfall 一樣的資源載入時間表

上面提到的幾個資訊，最重要的應該就是 Waiting 跟 Content Download 了，這兩個可能都代表著你的網路連線較慢或是伺服器的速度很慢，而 Content Download 很慢也有可能是請求的下載量太多了。檢查伺服器及網路狀況或是壓縮請求 (gip) 都可能會有幫助。

## 小結
今天我們算是把網路面版講完了，花了好幾天的時間，可是還是有很多內容沒有提到(遮臉)。不過我可以保證這些一定是最常用的功能XD
如果想要更多認識的朋友，老話一句，只能從[官方文件](https://developers.google.com/web/tools/chrome-devtools/network-performance/reference)下手啦，雖然有些欄位資訊官方好像也還有更新(看來大家都一樣，討厭寫文件冏)。接下來我們要一起來看審查面版 (Audits) 了，明天見！
