# 香港繁體中文網站

本網站使用 Hugo、Blowfish 及 Markdown 建置，並部署至 GitHub Pages。

## 本機預覽

請安裝 Hugo Extended 0.167.0，以及 Go 1.25 或以上版本。首次啟動時，Hugo 會按 `go.mod` 下載 Blowfish 主題。

```sh
hugo server
```

開啟 <http://localhost:1313/zh-hk/>。

## 編輯內容

- `content/_index.md` — 首頁及首頁介紹
- `content/biography.md` — 簡介
- `content/blog/_index.md` — 文章列表介紹
- `content/blog/` — 以 Markdown 撰寫的文章
- `config/_default/` — Hugo、Blowfish、語言及導覽設定
- `assets/css/custom.css`、`assets/img/` — 網站自訂樣式及主題圖片
- `public/assets/` — 網站圖片及圖示

新增文章時，在 `content/blog/` 建立 Markdown 檔案，並在檔案開首加入標題、日期、摘要及標籤等 front matter。
