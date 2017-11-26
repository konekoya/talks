
# 開發者工具快捷鍵跟設定

設定擷圖

## 幾個常用的快捷鍵
在這裡我想分享幾個我最常用到的快捷鍵，強迫自己使用快捷鍵可以讓自己的工作速度提昇，強列建議大家可以把你常用的快捷鍵背起來。如果你想要找特定的快捷鍵，官方文件有所有可用[快捷鍵的列表](https://developers.google.com/web/tools/chrome-devtools/shortcuts)。

- 打開 Chrome 開發者工具(打開後的面版會是上一次你離開開發者工具時正在使用的的那個面版)： Mac 使用 `Cmmand+Option+I`， Windows 使用 `F12 or Control+Shift+I`
  > 一個小技巧：打開開發者工具後，在任何面版，只要使用 `Esc` 鍵就可以打開開發者工具下的抽屜 (Drawer)，我通常使用這個指令來打控制台面版 (Console panel)

- 進入原素面版 (Elements panel)，並檢查頁面上的原素： Mac 使用 `Command+Shift+C`， Windows 使用 `Control+Shift+C`
- 搜尋面版： 我最常用於原素面版 (Elements panel) 及原始碼面版 (Sources panel)： Mac 使用 `Command+F`， Windows 使用 `Control+F`
  > 這個指令有幾個面版不支援：審查 (Audits) ，應用 (Application) 及安全性 (Security panels)
- 進入偏好設定頁面：Mac 使用 `? or Function+F1`， Windows 使用 `? or F1`

## 偏好設定
在這頁面中你可以調整很多設定來符合你個人的偏好，我會說明幾個我自己常用的。
- 快觀 (Appearance)：
    - 主題 Theme：主題有兩種可以選，如我個人偏好黑色的主題 (Dark) ，所以通常我會改成黑色的。如果想要其他主題，可以參考這個外掛 [DevTools Author](https://github.com/micjamking/devtools-author)

- 原始碼 (Sources)：
    - Enable JavaScript source maps：這應該是預設打開的，如果沒請記得打開，這樣可以讓你在除錯的時候可以看到還未打包成一個檔案前的檔案。如果你想了解更多關於，官方文件上[有一篇說明](https://developers.google.com/web/tools/chrome-devtools/javascript/source-maps)
    - Enable CSS source maps：應該預設是打開的，這個也是最好要保持打開的選項，這個功能是當你使用一些預處理器 (Preprocessors) 像是 SCSS 的時候，可以在開發者工具裡看到編譯前的.scss 檔，而不是編譯完後的檔案。

- 原素 (Elements)：
    - Color format：預設是按照來源 (As authored)，你也可以改成你偏好的顏色模式像是 HEX 或是 RGB

- 網路 (Newwork)
    - Disable cache (while DevTools is open)：關閉快取這個功能我都會打開，在開發時如果快取沒有每次清，常常會遇到很怪的臭蟲，所以我強列建議一定要打開這個選項，這個功能只有在開發者工具是打開時才有效。
    
- 控制台 (Console)
    - Preserve log upon navigation ：這個功能讓你可以在切換不同頁面時仍然可以看到先前頁面的 logs ，除錯的時候很方便，但是通常我不會打開，有需要時才會打開，不然頁面會有一堆 logs
