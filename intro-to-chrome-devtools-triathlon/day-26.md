# 記憶體面版 - 檢測分離 DOM 節點
昨天我們一起看了一段官方文件裡提供的程式，它會產生分離的 DOM 節點，這些節點不會被垃圾回收 (Garbage Collection) 所以會造成記憶體洩漏。今天我們一起來看如何透過開發者工具我們可以找到這樣的分離 DOM 節點。

> 今天使用的範例我放在 Codepen.io 上，[範例連結](https://codepen.io/konekoya/pen/vpyqby?editors=1010)

在打開範例網頁後，請先打開你的開發者工具並切換到記憶體面版。在這裡我們先選擇 **Take heap snapshot**，然後按下在下面的藍色按鈕 **Take snapshot**  來新增一個記憶體堆快照，這可能要花點時間讓它跑，在完成記憶體堆快照後，在介面左邊的 **Profiles** 列表裡會有我們剛剛做完的快照檔案。這個快照檔案裡有很多資訊，但是我們要找是的分離的 DOM 節點，我們可以過工具列上的 Class filter 來搜尋。請在搜尋框裡輸入 **Detached**，這樣在下方的列表應該就會出現這些 **Detached DOM tree** 如下圖：

![分離 DOM 節點擷圖]()

這邊我們先來說明一下這個列表欄位各自代表的意義 (官方文件有更詳細的[說明](https://developers.google.com/web/tools/chrome-devtools/memory-problems/heap-snapshots))：
- Constructor: 產生物件所使用的建構子，像是 `String`, `Array`, `Object` 等
- Distance: 物件到 `window` 也就是 root 的層級
- Objects count: 物件數量
- Shallow Size: 物件本身所佔用的記憶體大小
- Retained Size: 除了物件本身之外，包含它所關聯的其他物件所佔用的記憶體大小

