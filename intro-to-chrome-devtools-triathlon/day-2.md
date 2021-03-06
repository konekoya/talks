# 一點點前端除錯的歷史

![Software bug](https://www.dropbox.com/s/op0lcbvxuuqwkdp/bug.jpg?raw=1)
> 在早期電腦中發現真正的臭蟲


## 較早期的除錯方式


今天要來談談一點前端除錯的歷史。在開發者工具出來前，比較常見用來除錯的JavaScript 工具有 `alert` ，其實我猜就算到現在， `alert` 還是很多人在使用，但是用 `alert` 來除錯的效率是很差的，因為你的程式會一直需要中斷，而且你只能手動去把`alert` 關掉。想像一下，如果你有一個巢狀迴圈，然後你在第二層迴圈裡放了一個`alert` ，當迴圈每跑一次，你就需要去把它手動關掉直到迴圈完全跑完 XD。

另一個使用 `alert` 的問題在於，它無法顯示 JS 裡的物件，比如說：

```js
myObj = {
  a: 'A',
  b: 'B',
};
```

你如果嘗試著顯示這個物件在 `alert` 中，你會得到 [object object]。所以使用`alert` 來除錯很顯然是效率差且協助不大的方法。但是 `alert` 算是在 `console` 出現前，瀏覽器支援度最好的除錯方式，甚在 IE6, IE7 中都可以使用。

![object object 擷圖](https://www.dropbox.com/s/44s17s3shmi4oym/alert-object.jpg?raw=1)  
> alert 沒辦法顯示物件裡的內容

另一個除錯可以用到的工具，就是查看頁面的原始碼。這個頁面的原始碼其實就是你的瀏覽器從伺服器拿回來的頁面原始碼，但是還沒有經過瀏覽器解析過的，所以其實並不是真正的文件物件模型 (Document Object Model, DOM)，你看不到 JS 跑過後的內容，甚至樣式。因此這一個功能對於除錯來說，幫助也不大，更不要提早期在 IE 中，查看頁面原始碼是用筆記本打開的 ! 對，沒錯！你沒有看錯，真的是用筆記本打開的，所有的 HTML 原始碼都會變成沒有排版跟語法突顯 (Syntax highlighting) 的原始碼 … 這叫人怎麼看呢 XD

![nodepad 擷圖](https://www.dropbox.com/s/sbjvkj7l70ypv24/IE-page-source2.jpg?raw=1)
> IE 沒有內建原始碼預覽工具

## Firebug 的出現

![Firebug 擷圖](https://www.dropbox.com/s/rdprcw28qbvf0p0/firebug-large.png?raw=1)  
> Firebug logo

之後，在 Firefox 上面出現了一個完全改變開發者除錯甚至開發方式的插件 (Add-ons)，那就是 [Firebug](https://getfirebug.com/) ， Firebug 提供一個類似現在開發者工具的介面，你可以在上面動態 (Live) 修改 HTML, CSS, 甚至 JS ，還記得那時候我跟同事們的開發方式從原本用編輯器來寫 CSS 然後再重整瀏覽器來看樣式套用後的效果改成直接寫在 Firebug 的編輯器裡，在看到樣子套用上去的效果之後，再把程式貼回編輯器裡，因為這樣的工作流程更快而且更準確，不需要去猜說，樣式套上去後會長怎樣。

## 現代開發者工具

在 Firebug 之後就是 Chrome 的開發者工具的出現。從此之後，開發者工具就一直演進到現在，除了可以動態修改原始碼之外，也多了很多更強大的開發工具，比如：動畫(Animation) 的狀態查看、網路面版 (Network panel)，讓你可以看到所有資源透過 HTTP 傳送的狀態，效能面版 (Performace)，讓你可以檢查記憶體跟 CPU 的使用狀態等，這些功能我們會陸續在這系列中介紹。

好了，現在我們對整個前端的除錯歷史已經有一點了解，讓我們開始進入開發者工具的介紹吧！
