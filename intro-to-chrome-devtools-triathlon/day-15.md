
# 應用面版
在 HTML5 的標準裡面，加入了很多以前所沒有的前端儲存方式像是 Local and session storage, IndexedDB 等等。而 Chrome 開發者工具為了方便開發者可以存取及編輯這些儲存方式，提供了一個應用面版 (Application panel)，今天我們要來介紹如果透過這個面版來檢查、修改及刪除這些儲存方式，但我們會主要針對 Local storage 及 cookies，其他的幾個儲存方式我沒有使用過，如果你想更深入的了解，你可以在官方文件裡找到[使用說明](https://developers.google.com/web/tools/chrome-devtools/manage-data/local-storage)。

## 應用面版介面簡介


## 檢視及編輯 Local storage
你可以檢視你的網頁所使用的 Local storage 資訊，打開左邊側欄的 Local Storage，在這邊會有可用的網域列表，選擇你所想要查看的網域。Local storage 所儲存的資訊是用鍵及值 (key-value pairs) 來做存放。你可以在列表中看到所有儲存在 Local storage 的資料，你也可以透過上方的 Filter 來搜尋特定的鍵及值。

- 編輯鍵及值：在你想要編輯的鍵或值用滑鼠左鍵點兩下或是用鍵盤的 enter 鍵來進入編輯模式，在編輯後用滑鼠在編輯區域外點一下或是再按一次 enter 鍵就可以完成編輯。

- 刪除鍵及值：選定要刪除的資料後，使用鍵盤的 delete 鍵或是工具列上的刪除按鈕來刪除這一筆資料。如果你想清除所有 Local storage 裡的資料的話，可以使用上方工具列的清除按鈕來清除所有資料。

- 新增一筆資料：在資料列表的最下方空白處用滑鼠連點兩下就可以新增一筆新的資料 

> 上述的新增、刪除、尋找及編輯的功能其實也都可以透過 JavaScript 來完成，如果你打開控制台抽屜 (Console drawer)，直接使用 HTML API 來操作，這些操作的結果都會立即更新到 Local storage 列表中
