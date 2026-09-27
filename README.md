# Block Tower website

這個目錄包含可直接部署的靜態產品首頁、隱私政策與支援中心頁面：

- `index.html`：產品首頁，含 App Store 上架前 CTA、玩法介紹與 Open Graph metadata。
- `privacy.html`：App Store Connect 可使用的隱私政策頁面。
- `support.html`：支援 FAQ、購買協助與問題回報方式。
- `styles.css`：三頁共用的響應式樣式。
- `assets/app-icon.png`、`assets/app-icon-dark.png`：以 iOS 正式淺色／深色圖示製作的網站版本，四角採透明圓角；iOS 原始圖示不變。
- `assets/favicon-*.png`、`assets/pwa-icon-*.png`：使用相同透明圓角的瀏覽器與可安裝網站圖示尺寸。
- `assets/apple-touch-icon.png`：保留方形原圖，讓 iOS 主畫面套用系統圓角遮罩。
- `assets/hero-iphone.png`、`assets/og.png`：產品首頁裝置預覽與社群分享圖。
- `site.webmanifest`：網站名稱、顏色及可安裝網站圖示設定。

## 上線前待替換項目

`support@blocktower.app` 是可讀、可替換的客服信箱 placeholder；正式上架前請換成團隊實際監控的信箱，並確認 `blocktower.app` 網域已指向正式網站。App 內的隱私與支援連結也預設使用：

- `https://blocktower.app/privacy`
- `https://blocktower.app/support`

如果正式部署使用不同網域，請同步更新 AppShellView 的連結與 App Store Connect 的隱私政策／支援網址。App Store 連結確認後，再把首頁 `#download` 的「即將上架」CTA 換成正式商店連結。
