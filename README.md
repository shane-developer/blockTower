# Block Tower｜跨平台整合版

這份資料夾是目前最完整的 iOS 與 Android 專案整合版，Android 採用目前支援摺疊機的主線，iOS 採用具完整主題、購買相容性與隱私資料的版本。兩平台都支援英文與繁體中文，英文為預設／主要語言，並依裝置語言顯示繁中。原本的 `BlockTower/`、`android/` 與 `意外發現/` 都保留未覆寫。

## 專案內容

- `iOS/`：Xcode 專案、SwiftUI／SpriteKit 遊戲、12 組主題、StoreKit 2、測試與 `PrivacyInfo.xcprivacy`。
- `Android/`：Kotlin／libGDX／Box2D 遊戲、13 種多格積木、五種模式、手機／平板／摺疊姿勢適配、測試與 F-Droid 發布範本。Android 不提供應用程式內購買；Bolt 仍作為遊戲內資源。
- `Design/`：遊戲設計與九宮格視覺規格。
- `website/`：網站、隱私政策、支援頁與品牌素材。
- `Marketing/`：英文與繁體中文的 App Store iPhone／iPad 宣傳圖、社群素材與產圖腳本；20 張上架 JPEG 已完成尺寸與無 alpha 檢查，操作方式見 [Marketing/README.md](Marketing/README.md)。
- `驗收用/BlockTower-Android-debug.apk`：目前 Android 主線建置的本機驗收 APK（debug key 簽署）。
- `驗收用/AppStore-Screenshots-en-US-zh-Hant.zip`：20 張英文／繁中、iPhone／iPad 上架 JPEG，已按語系與裝置分資料夾打包。
- `MERGE_NOTES.md`：來源選擇、整合原則與發布前待補資料。

## 建置 iOS

需求：Xcode、iOS 17 或更新版本的 Simulator SDK。

```sh
cd iOS
xcodebuild -project BlockTower.xcodeproj -scheme BlockTower \
  -sdk iphonesimulator -configuration Debug \
  CODE_SIGNING_ALLOWED=NO build
```

在 Xcode 選擇 `BlockTower` scheme 與 iOS Simulator 也可直接執行。

## 建置 Android

需求：JDK 17、Android SDK Platform 36 與 Build Tools 36。

```sh
cd Android
./gradlew :app:testDebugUnitTest :app:assembleDebug
```

Debug APK 會產生於 `Android/app/build/outputs/apk/debug/app-debug.apk`。`local.properties` 不隨專案提供；讓 Android Studio 指定 SDK，或在建置環境設定 `ANDROID_HOME`／`ANDROID_SDK_ROOT`。

Android 支援 `arm64-v8a`、`armeabi-v7a`、`x86_64`。BOOK 姿勢是同一個全幅遊戲畫面；TABLETOP 將棋盤與托盤放在鉸鏈上下兩側。

## 商店與授權狀態

iOS 保留 StoreKit 商品和舊永久主題購買的相容性。Android 不包含 Play Billing 或其他 App 內付款。Android 的 `LICENSE-DRAFT.md` 仍是草稿，F-Droid GitHub owner/tag 與 repository URL 仍需依發布方式設定；網站聯絡管道統一使用 [Google 表單](https://forms.gle/gVLRwAY1yRQqvcTY8)。iOS 隱私政策連結使用 Vercel 主機名稱 `blocktower-lac.vercel.app`。

Android 第三方依賴清單與授權來源見 `Android/THIRD_PARTY_NOTICES.md`；Noto Sans TC 字型的 OFL 文字隨字型放在 `Android/app/src/main/assets/fonts/OFL.txt`。

## 驗收紀錄

整合資料夾是在保留兩份既有版本的前提下建立。Android 單元測試／Debug build 與 iOS Simulator build 的本次結果會記錄在 `MERGE_NOTES.md`，並清楚區分已驗證及需要實機／發布帳號才能完成的項目。

## English quick start

This folder combines the latest verified iOS and Android project snapshots. Both apps support English and Traditional Chinese; English is the default and primary language, with Traditional Chinese selected from the device language. `iOS/` contains the 12-theme SwiftUI/SpriteKit app and its Xcode project. `Android/` contains the foldable-aware Kotlin/libGDX game; Android has no in-app purchases, while Bolt remains an in-game resource. The iOS app retains StoreKit 2 and legacy purchase compatibility. Upload-ready English and Traditional Chinese App Store screenshots for iPhone and iPad are in `Marketing/AppStore/` and in `驗收用/AppStore-Screenshots-en-US-zh-Hant.zip`.

Build iOS from `iOS/` with the `BlockTower` Xcode scheme. Build and run Android checks from `Android/` with `./gradlew :app:check`; the project uses JDK 17 and Android SDK 36. A locally signed Debug APK is available at `驗收用/BlockTower-Android-debug.apk`. It is for device acceptance only, not store release.
