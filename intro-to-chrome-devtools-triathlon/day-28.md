
# 記憶體面版 - 記憶體分配分析器
今天我們要介紹的工具是記憶體面版中的最後一個工具: **Record Allocation Profiler**，這個工具可以讓我們按函數來檢視說那些函數佔用了許多記憶體，也可以讓我們直接追回原始碼。

> 我們今天使用的範例是昨天的程式碼，你可以在 Codepen.io 上找到這個[範例](https://codepen.io/konekoya/pen/LeWVbO)

在開始前我們一樣先打開 Chrome 開發者工具然後切換到記憶體面版 (Memory panel)，再選用我們今天要使用的工具 **Record Allocation Profiler**，最後再按下 **Start** 按鈕。這時候它就會開始錄制記憶體的使用狀況，現在點擊頁面上的 **Create memory leaks** 按鈕幾次，然後再用工具列上的停止錄制按鈕或是中間的 **Stop** 按鈕來停止錄制。在停止錄制後你就會得到一份報告，它也會出現在左邊的列表中。這份報告會類似下圖：

![報告擷圖]()
