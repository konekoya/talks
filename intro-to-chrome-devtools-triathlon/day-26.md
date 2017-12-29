# 記憶體面版 - 記憶體堆快照 2
昨天我們一起看了一段官方文件裡提供的程式，它會產生分離的 DOM 節點，這些節點不會被垃圾回收 (Garbage Collection) 所以會造成記憶體洩漏。今天我們一起來看如何透過開發者工具我們可以找到這樣的分離 DOM 節點。

> 今天使用的範例我放在 Codepen.io 上，[範例連結](https://codepen.io/konekoya/pen/vpyqby?editors=1010)

在打開範例網頁後，請先打開你的開發者工具並切換到記憶體面版。在這裡我們先選擇 **Take heap snapshot**，然後按下在下面的藍色按鈕 **Take snapshot**  來新增一個記憶體堆快照，產生這個快照要花一點時間，在完成記憶體堆快照後，在介面左邊的 **Profiles** 列表裡會有我們剛剛做完的快照檔案。這個快照檔案裡有很多資訊，但是我們要找是的分離的 DOM 節點，我們可以過工具列上的 Class filter 來搜尋。請在搜尋框裡輸入 **Detached**，這樣在下方的列表應該就會出現這些 **Detached DOM tree** 如下圖：

![分離 DOM 節點擷圖](https://www.dropbox.com/s/gn43c946otxtu9n/detached.jpg?raw=1)
**圖 1** : 目前頁面上所有的分離 DOM 節點

這邊我們先來說明一下這個列表欄位各自代表的意義 (官方文件有更詳細的[說明](https://developers.google.com/web/tools/chrome-devtools/memory-problems/heap-snapshots))：
- Constructor: 產生物件所使用的建構子，像是 `String`, `Array`, `Object` 等
- Distance: 物件到 `window` 也就是 root 的層級
- Objects count: 物件數量
- Shallow Size: 物件本身所佔用的記憶體大小
- Retained Size: 除了物件本身之外，包含它所關聯的其他物件所佔用的記憶體大小

在展開分離的 DOM 節點後，你應該會發現有些元素會有紅色的背景，這代表它們是沒辦法被垃圾回收的 DOM 節點，它們沒有直接被 JS 引用，而黃色節點則是有直接的 JS 引用。

![展開的 DOM 節點擷圖](https://www.dropbox.com/s/5ztaq0gkf29xafn/expanded.jpg?raw=1)  
**圖 2** : 展開分離的 DOM 節點裡有紅色及黃色的節點


好，我們現在看到的這些分離的 DOM 節點其實都是 Codepen.io 本身的，現在我們要透過我們的程式來產生分離的 DOM 節點。請按下我們頁面上的 **Create detached list** 按鈕，然後再使用工具列上的錄制按鈕![錄制按鈕擷圖](https://www.dropbox.com/s/7e63hrtau3v8i7q/record.jpg?raw=1)再產生一份新的記憶體堆快照。完成後你現在應該會有兩份記憶體堆快照

![分離 DOM 節點擷圖]()

在第二份快照裡，一樣我們在搜尋框裡輸入 **Detached** ，你會發現列表裡多了一份 **Detached DOM tree / 11 entries**，展開後你會發現它是 `HTMLUListElement` 就是我們用 `create` 方法產生的 `ul` 元素

## 小結
透過記憶體堆快照我們可以發現這些分離的 DOM 節點，這個過程其實很快，但是修正的部份反而是比較難的，因為這個工具只能讓我們知道有哪些 DOM 元素是已經被分離，沒有真正在使用，但是在一個大專案裡，我們可能有許多 DOM 元素的操作，也會有很多第三方的程式在做這樣的操作。所以檢測算是簡單的一步，真正困難的部份在於修正。不過至少我們已經知道第一步了XD，接下來我們要介紹記憶體工具的其他工具，明天見！
