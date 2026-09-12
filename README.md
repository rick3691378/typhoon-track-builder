# 🌀 颱風路徑製作工具 Typhoon Track Builder

一個完全在瀏覽器端運作、免安裝、免後端的颱風路徑繪製與警報圖製作工具。單一 HTML 檔案即可使用，內建互動地圖、強度自動判定、暴風圈繪製、颱風警戒海面／縣市標示，並能一鍵匯出成類似官方風格的「颱風警報圖」與「颱風路徑圖」（PNG 或 PDF）。

> ⚠️ 本工具產出的所有圖表皆為**使用者自行輸入資料產生**，僅供參考、教育與示意用途，**非中央氣象署或其他機關之正式發布資料**。

---

## ✨ 功能特色

### 路徑點編輯
- 支援手動輸入座標，或直接在地圖上點選經緯度
- 每個測站點可記錄：時間、氣壓 (hPa)、最大風速 (kt)、七級風暴風半徑、十級風暴風半徑
- 標記「實測」或「預測」點 — 已發生路徑以**實線**呈現，尚未發生的預測路徑自動以**虛線**呈現
- 測站點清單支援編輯、刪除、上下移動、依時間排序

### 強度自動判定
- 依風速自動分類為熱帶性低氣壓 / 輕度颱風 / 中度颱風 / 強烈颱風（可手動覆寫）
- 路徑線與測站點依強度自動上色

### 暴風圈與地圖顯示
- 可繪製七級風與十級風暴風半徑圈，並直接在圖上標示公里數
- 底圖可切換淺色／深色（Esri Light/Dark Gray Canvas，免金鑰、可公開嵌入使用）
- 可調整路徑線寬、是否顯示測站編號

### 颱風警報模式
- 內建 8 個海上颱風警報警戒海面（依方位角概略示意，非精確海域界線）
- 內建全台 22 縣市真實行政區界線（資料來源：[g0v/twgeojson](https://github.com/g0v/twgeojson)），可勾選標示陸上颱風警報警戒縣市
- 警戒範圍會自動反映在匯出的圖表標題與圖例中

### 匯出 / 匯入
| 格式 | 說明 |
|---|---|
| **JSON** | 完整保存路徑資料、颱風資訊、警戒區域設定，可再次匯入繼續編輯 |
| **GeoJSON** | 相容 QGIS、ArcGIS 等 GIS 軟體 |
| **PNG / PDF 警報圖** | 含標題、比例尺、指北針、強度圖例、各測站點資料表 |
| **PNG / PDF 路徑圖** | 同上但不含資料表，版面較簡潔 |

匯出圖表以 3 倍解析度渲染，適合列印或投影使用。

---

## 🚀 使用方式

### 方法一：直接下載使用
1. 下載本專案的 [`typhoon-track-builder.html`](./typhoon-track-builder.html)
2. 用瀏覽器直接開啟該檔案即可使用，不需要任何安裝或伺服器

### 方法二：透過 GitHub Pages
若已啟用本專案的 GitHub Pages，可直接以瀏覽器開啟：
```
https://rick3691378.github.io/typhoon-track-builder/typhoon-track-builder.html
```
（請依實際部署路徑調整網址）

### 方法三：本機起一個簡單伺服器
```bash
git clone https://github.com/rick3691378/typhoon-track-builder.git
cd typhoon-track-builder
python3 -m http.server 8000
# 瀏覽器開啟 http://localhost:8000/typhoon-track-builder.html
```

---

## 🧱 技術棧

- 純 HTML / CSS / JavaScript（無框架、無建置流程）
- [Leaflet](https://leafletjs.com/) — 互動地圖
- [html2canvas](https://html2canvas.hertzen.com/) — 地圖截圖
- [jsPDF](https://github.com/parallax/jsPDF) — PDF 匯出
- Esri Light/Dark Gray Canvas — 底圖圖磚
- 內嵌台灣縣市邊界資料（來源：g0v/twgeojson，已簡化以縮小檔案大小）

所有第三方套件皆透過 CDN 載入，需要網路連線才能顯示底圖與匯出圖片/PDF；路徑點資料的編輯與 JSON/GeoJSON 匯出則不需要網路。

---

## 📁 檔案結構

```
typhoon-track-builder/
├── typhoon-track-builder.html   # 主程式（單一檔案，包含全部功能）
└── README.md
```

---

## ⚠️ 已知限制

- 底圖為 Esri 提供之免費公開圖磚，並非開放原始碼服務，且非高解析度導航等級資料
- 海上颱風警報警戒海面為方位角示意繪製，**非**中央氣象署正式海域界線
- 陸上颱風警報縣市邊界資料為簡化版本，非精確測量等級的行政區圖資
- 所有資料皆由使用者手動輸入，本工具不會、也無法查詢即時颱風資訊

---

## 📄 授權 License

本專案採用 [MIT License](./LICENSE)（如尚未加入 LICENSE 檔案，請自行新增）。地圖資料版權分屬各自來源（Esri、OpenStreetMap 貢獻者、g0v/twgeojson），使用時請遵循其各自的使用條款。

---

## 🤝 貢獻

歡迎透過 Issue 或 Pull Request 提出功能建議與回報問題。
