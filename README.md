# 機車 & ATV／UTV 知識庫（產業動態 Dashboard）

一個可部署於 **GitHub Pages** 的靜態單頁式產業知識庫專案，涵蓋二輪機車與特殊載具（ATV／UTV）的：
- **📰 最新動態**（`#activity`）
- **🗺️ 概念地圖**（`#concepts`）
- **🌍 國家動態**（`#countries`）
- **🏭 車廠資料庫**（`#entities`）
- **📚 來源追蹤**（`#sources`）

## 專案結構

```text
moto-atv-wiki/
├── .github/workflows/deploy.yml   # GitHub Actions 自動建置與發布流程
├── content/                       # 知識庫資料（JSON 格式，直接編輯即可擴充）
│   ├── activities.json
│   ├── concepts.json
│   ├── countries.json
│   ├── entities.json
│   └── sources.json
├── templates/index.template.html  # 前端儀表板樣板
├── scripts/build.py               # 建置腳本（純 Python 標準函式庫，免安裝套件）
├── index.html                     # 編譯完成的靜態首頁
└── .nojekyll                      # 停用 Jekyll 以直接服務靜態檔案
```

## 本機預覽與更新資料

1. 修改 `content/` 資料夾底下的任一 `.json` 檔案（例如新增車廠或來源）。
2. 在專案根目錄執行建置腳本：
   ```bash
   python3 scripts/build.py
   ```
3. 直接用瀏覽器開啟 `index.html`，或啟動簡易本機伺服器預覽：
   ```bash
   python3 -m http.server 8080
   ```

## 如何對外發布成公開網址（GitHub Pages）

1. 在 GitHub 建立一個新的公開儲存庫（Repository），例如 `moto-atv-wiki`。
2. 將本專案所有檔案上傳或 `git push` 至 `main` 分支：
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Moto & ATV/UTV Wiki"
   git branch -M main
   git remote add origin https://github.com/<你的帳號>/moto-atv-wiki.git
   git push -u origin main
   ```
3. 進入儲存庫的 **Settings → Pages**，將 **Source** 選擇為 **GitHub Actions**。
4. 等待約 30 秒後，即可透過 `https://<你的帳號>.github.io/moto-atv-wiki/` 對外分享與連結使用。
