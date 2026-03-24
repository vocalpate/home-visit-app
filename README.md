🏥 居家醫療管理系統
中醫居家訪視個案管理 Web App，支援手機與電腦使用。
App 網址： `https://vocalpate.github.io/home-visit-app/`
---
功能說明
新增、編輯、刪除個案資料
欄位：姓名、病歷號、電話、住址、緊急聯絡人、聯絡人電話、收案團隊、收案日期、結案日期、備註
結案日期預設為收案日期 +365 天（可手動修改）
結案日距今 30 天以內，自動顯示黃底警示 ⚠️
依病歷號、姓名、收案日、結案日排序
病歷號空白時，自動改用收案日期遞補排序；兩者皆空白則依姓名排序
支援姓名、病歷號、電話關鍵字搜尋
---
手機加入主畫面（像 APP 一樣使用）
iPhone / iPad：
用 Safari 開啟 App 網址
點下方分享按鈕 □↑
選「加入主畫面」
點「新增」
Android：
用 Chrome 開啟 App 網址
點右上角三個點 ⋮
選「新增至主畫面」
---
Google Drive 同步設定
個案資料可同步至 Google Drive（每位個案獨立一份試算表）及 Google Sheets 總覽名單。
第一步：建立 Google Apps Script
前往 script.google.com，建立新專案
將 `gas-script.js` 的程式碼貼入
修改程式碼中的 `FOLDER_ID`（Google Drive 資料夾 ID）與 `SHEET_ID`（Google Sheets 試算表 ID）
點選「部署 → 新增部署」
類型選「網頁應用程式」
執行身分選「我」，存取權限選「任何人」
複製部署網址（格式為 `https://script.google.com/macros/s/.../exec`）
第二步：填入 App 設定
開啟 App，點右上角 ⚙️
將部署網址貼入欄位
點「儲存」
設定完成後，每次新增或編輯個案，資料會自動同步至 Google Drive。
---
更新 App
如需更新程式（例如修改排序邏輯、新增欄位）：
從 Claude 下載新版 `index.html`
進入此 GitHub 儲存庫
點 `index.html` → 右上角 ✏️ 編輯（或直接上傳覆蓋）
Commit changes
等約 1～2 分鐘，網址自動更新
---
資料儲存說明
狀態	資料存放位置
未設定 GAS 網址	瀏覽器本機（localStorage）
已設定 GAS 網址	瀏覽器本機 ＋ Google Drive 同步
> 注意：清除瀏覽器資料會導致本機資料消失，建議完成 GAS 設定以確保資料安全。
---
排序邏輯
排序方式	規則
病歷號	有病歷號的排前，空白的依收案日遞補，皆空白則依姓名
姓名 / 收案日 / 結案日	空白值一律排最後
