# daily_dashboard

### 第一步:Notion 端

到 notion.so/my-integrations 建立一個 Integration,複製它的 secret
在 Notion 建一個資料庫,包含三個欄位:名稱(標題型)、日期(日期型)、完成(核取方塊)——如果你想用不同的欄位名稱也可以,之後在 Worker 環境變數裡改
在該資料庫頁面右上角「···」→ 連接(Connections)→ 加入你剛建立的 Integration
從資料庫網址複製 32 碼的資料庫 ID

### 第二步:部署 Cloudflare Worker

註冊 Cloudflare(免費),進 Workers & Pages → 建立 Worker
把 worker.js 的內容全部貼進去,部署
在 Worker 的 Settings → Variables 加入兩個 Secret:NOTION_TOKEN 和 NOTION_DB_ID
直接用瀏覽器打開 Worker 網址測試,應該會看到 JSON 格式的待辦清單

### 第三步:儀表板上線

打開 dashboard.html,把最上面 CONFIG 區塊的 WORKER_URL 改成你的 Worker 網址,LAT/LON 改成你的所在地座標(預設是台北)
把這個檔案放上 GitHub Pages(建一個 repo、上傳、開啟 Pages 功能即可)

### 第四步:HyRead Gaze 端

側載 Fully Kiosk Browser 的 APK(它專門做全螢幕看板,還能設定保持螢幕常亮)
把 Start URL 設成你的 GitHub Pages 網址,開啟 Keep Screen On
