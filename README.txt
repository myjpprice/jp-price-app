# 🛒 日本逛街購物小清單 (Japanese Shopping OCR & Price Tracker)

一個專為赴日旅遊設計的網頁型 OCR 購物小清單工具。透過手機拍照或上傳商品/價牌照片，自動辨識商品名稱、價格，並利用 **AI 座標辨識（Bounding Box）** 與 **HTML5 Canvas** 自動將每個商品局部裁切成特寫縮圖，讓你在日本逛街時比價、記帳更直覺！

---

## 🌟 主要功能特色

- **📸 輕鬆上傳/拍照**：支援手機直接拍照或上傳截圖，自動發送至後端進行辨識。
- **🤖 AI 智慧辨識 (Gemini 3.6 Flash)**：串接 Google Gemini API，精準解析日本商品的複雜包裝、漢字與價格標籤。
- **✂️ 自動局部裁切預覽**：AI 回傳商品位置座標（`box_2d`），前端透過 HTML5 Canvas 自動裁切出該商品的獨立局部縮圖，顯示於清單旁。
- **⚡ 輕量化架構**：
  - **前端**：託管於 GitHub Pages (`index.html`)。
  - **後端**：使用 Cloudflare Workers 處理 API 請求與 AI 溝通，安全且免維護伺服器。

---

## 🛠️ 專案架構

```text
├── index.html        # GitHub Pages 前端介面（含 UI、上傳、Canvas 裁切邏輯）
└── worker.js         # Cloudflare Worker 後端（處理 Base64 轉換、串接 Gemini API 與回傳 JSON 座標）



日本購物查價 V1
1. 開啟 index.html 即可使用。
2. 商品資料與圖片儲存在本機瀏覽器 localStorage，無網路也可查詢。
3. 「匯出」可備份 JSON；換裝置時可用「匯入」恢復。
4. 若要在 iPhone 上做成主畫面 App：用 Safari 開啟這個網頁並選「加入主畫面」。
注意：目前圖片會直接儲存在瀏覽器資料中；大量高解析照片會增加儲存空間。
