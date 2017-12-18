
# 應用面版
在 HTML5 的標準裡面，加入了很多以前所沒有的前端儲存方式像是 Local and session storage, IndexedDB 等等。而 Chrome 開發者工具為了方便開發者可以存取及編輯這些儲存方式，提供了一個應用面版 (Application panel)，今天我們要來介紹如果透過這個面版來檢查、修改及刪除這些儲存方式，但我們會主要針對 Local storage 及 cookies，其他的幾個儲存方式我沒有使用過，如果你想更深入的了解，你可以在官方文件裡找到[使用說明](https://developers.google.com/web/tools/chrome-devtools/manage-data/local-storage)。

## 應用面版介面簡介
應用面版是兩欄式的介面，左邊有所有可選用的項目，點選後，右邊的欄位就會顯現選項內容。

![應用面版介面擷圖](https://www.dropbox.com/s/7mkb80cy4h60btg/application.jpg?raw=1)
**圖 1**: 應用面版的介面

## 檢視及編輯 Local storage
你可以檢視你的網頁所使用的 Local storage 資訊，打開左邊側欄的 Local Storage，在這邊會有可用的網域列表，選擇你所想要查看的網域。Local storage 所儲存的資訊是用鍵及值 (key-value pairs) 來做存放。你可以在列表中看到所有儲存在 Local storage 的資料，你也可以透過上方的 Filter 來搜尋特定的鍵及值。

- 編輯鍵及值：在你想要編輯的鍵或值用滑鼠左鍵點兩下或是用鍵盤的 enter 鍵來進入編輯模式，在編輯後用滑鼠在編輯區域外點一下或是再按一次 enter 鍵就可以完成編輯。

- 刪除鍵及值：選定要刪除的資料後，使用鍵盤的 delete 鍵或是工具列上的刪除按鈕![刪除按鈕擷圖](https://www.dropbox.com/s/4gnwcgnf4hh6cv8/delete.jpg?raw=1)來刪除這一筆資料。如果你想清除所有 Local storage 裡的資料的話，可以使用上方工具列的清除按鈕![清除按鈕擷圖](https://www.dropbox.com/s/p5cjh7fpx9g430z/clear-all.jpg?raw=1)來清除所有資料。

- 新增一筆資料：在資料列表的最下方空白處用滑鼠左鍵連點兩下就可以新增一筆新的資料 

![檢視及編輯 Local storage擷圖](https://www.dropbox.com/s/031jw92g3m6nhsw/local-storage.jpg?raw=1)
**圖 2**: 檢視及編輯 Local storage

> 上述的新增、刪除、尋找及編輯的功能其實也都可以透過 JavaScript 來完成，如果你打開控制台抽屜 (Console drawer)，直接使用 HTML API 來操作，這些操作的結果都會立即更新到 Local storage 列表中


## 檢視及編輯 cookies
從左邊的側欄打開 Cookies 後，它一樣會有網域列表，選取你想要檢視的網域後，就會看到在這個網域中所有有用到的 cookies 列表。這個列表裡有幾個項目：
- Name: cookie 的名稱
- Value: cookie 的值
- Domain: cookie 的 domain
- path: cookie 的路徑
- Expires/ Maximum Age: cookie 到期時間
- Size: cookie 的大小
- HTTP: 如果這個值是勾選的，那這個值無法透過 JavaScript 直接做修改
- Secure: 這個 cookie 需要透過加密連結來做傳輸

cookie 的編輯、刪除、新增方式都與上面提到的 Local storage 相同，所以在這邊我們就不再做說明。

![檢視及編輯 cookies 擷圖](https://www.dropbox.com/s/3oa4vjj8pbc243i/cookies.jpg?raw=1)
**圖 3**: 檢視及編輯 cookies

## 清除所有儲存及快取
如果你想一次清除所有前端所使用到的儲存資料及快取，你可以透過 Clear storage 來完成。在選取 Clear storage 後，在列表中選取你想清除的項目，然後使用 Clear site data 來清除所有的儲存資料。

![清除所有儲存及快取擷圖](https://www.dropbox.com/s/q1xpxwksldlv6fm/clear.jpg?raw=1)
**圖 4**: 在 Clear storage 選項中清除所有儲存及快取

## 查看資源
你可以透過左邊側欄的 Frames 來查看這個網頁或是應用程式所有的資源，像是 JavaScript, 圖片或甚至字型檔案，都可以在這邊做檢視。以前開發者工具功能比較陽春的時候，我會常常來這裡找一些檔案，不過現在就很少用到這個功能了。

![查看資源擷圖](https://www.dropbox.com/s/s4gffv8zicnsy4c/frames.jpg?raw=1)
**圖 5**: 使用查看資源來尋找頁面所用到的圖片檔 

## 小結
今天我們很快的一起看過應用面版，其實這個面版的主要功能就是讓你來檢視及修改你的應用程式有用到的一些前端儲存方式。如果你有用到這些儲存方式，透過這個面版就可以很快速的來除錯及知道你儲存資料的狀態。雖然有幾個不同的儲存方式我們沒有講到，但是其實操作都大同小異，像是 Session storage 的操作方式就跟 Local storage 完全相同。在講完這個面版後，接下來我們要花幾天的時間來講原始碼面版 (Sources panel)，這個面版可以大大的提升我們除錯的效率，讓我們快速的找到問題並修正。好，廢話不多說，我們明天見啦。
