# 前言

前端工程在過去這幾年變化快的驚人，JavaScript 從原先在頁面上只負責簡單的介面互動操作，到現在像是 SPA (Single Page Application) 架構，幾乎所有的頁面都是由JavaScript 生成，前端工程師所需要撰寫及維護的 JavaScript 程式越來越多。面對這麼多的 JS 原始碼，我發現良好的架構、測試及工具像是 ESLint 都是可以協助讓開發及維護變的更輕鬆。而在這當中還有一項重要的工具，也是我們這一系列要介紹的：開發者工具。

開發者工具對於前端工程師來說，我覺得就像是後端的 IDE ，可以下中斷點 ( 或debugger 在你的程式碼裡 )，查看程式在這個中斷點的作用範圍 (Scope)，狀態的變化甚至直接編輯及修改程式，然後再執行等等。我認為開發者工具是我所有技術的學習投資中，算是報酬率很高的一項工具，當你學會了如何善用這個工具，你的工作會變的更加輕鬆，
除錯 (Debug) 的時間可以大幅縮短 ( 雖然使用開發者工具並不保證一定可以找到 bug XD)

在這個系列中，我希望可以分享開發者工具的一些主要功能，因為開發者工具可以做的事情實在太多了，而且蠻多功能我甚至也沒用過冏

## 為什麼要用 Chrome 開發者工具來介紹

![DevTools image](https://www.dropbox.com/s/5my4vfs1ah3z3mn/chrome-devtools-16x9.png?raw=1)

而我們要使用的開發者工具是 Chrome 的開發者工具 (Chrome Developer Tools) 老外常簡寫為 DevTools 。為什麼選擇 Chrome 呢？因為 Chrome 的開發者工具是我最熟悉的，再來就是 Chrome 的開發者工具演進的非常快，新功能是一直不斷的增加，老實說，它的介面也一直不變的在變化。但是我想就算你是使用其他的開發者工具像是 IE 或是 Firefox ，除了介面之外，很多功能及概念都是相同的。

> 因為 Chrome 的更新頻率非常高並且開發者工具的使用者介面也常常在更動，所以在這個教學裡面提到的功能位置或是頁面擷圖，是會有可能與你實際使用的版本不同的。這個教學的寫作期間所用的是 Chrome 62.x

## 會討論到的主題

下面就是我們暫定接下來三十天的主題列表，之後有可能會再做調整，如果有任何更新的話我會再回來更新這個列表。

1. 什麼是開發者工具
2. 一點點前端除錯的歷史
3. 開發者工具面版簡介 - 1
4. 開發者工具面版簡介 - 2
5. 開發者工具面版簡介 - 3
6. 開發者工具快捷鍵跟設定
7. 元素面版 - 編輯 DOM
8. 元素面版 - 編輯 CSS
9. 元素面版 - 編輯 DOM 1
10. 元素面版 - 編輯 DOM 2
11. 元素面版 - 編輯 CSS 1
12. 元素面版 - 編輯 CSS 2
13. work with console 1
14. work with console 2
15. device mode
16. Application panel
17. source panel - 中斷點
18. source panel - 如何除錯
19. source panel - 其他除錯技巧
20. network panel - 1
21. network panel - 2
22. network panel - 3
23. profile - 1
24. profile - 2
25. memory - 1
26. memory - 2
27. audits - 1
28. audits - 2
29. real case - 1
30. real case - 2
31. concultion
