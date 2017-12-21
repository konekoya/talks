# 網路面版 - 了解每個請求
經過這幾天的介紹，我想大家對這個面版已經有一定的認識了，但是我們其實還沒有進到每個 HTTP 請求裡面，去查看這個請求細節，而這就是我們今天要做的。好，就讓我們一起開始吧！

## 進入請求細節
一開始我們一樣先打開 Chrome 開發者工具然後切換網路面版 (Network)，這時候你的頁面可能不會有完整的 HTTP 請求列表，請重新整理一下你的頁面，你應該就會得到一個完成的 HTTP 請求列表在你網路面版裡面。

> 今天我們用的範例網站一樣是 [iT 邦幫忙的首頁](https://ithelp.ithome.com.tw/)

我選用的 HTTP 請求是 `ithelp.ithome.com.tw` 的 `document` 文件。在用滑鼠左鍵點擊後，它會在請求的右邊打開一個新的頁面，如下圖：

!(請求細節擷圖)[]


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
