# 荒野中的呼喊者

以繁體中文記錄生活與想法的個人網站，使用 [Hugo](https://gohugo.io/) 和 [Blowfish](https://blowfish.page/) 建置，並透過 GitHub Pages 託管。

[![部署至 GitHub Pages](https://github.com/voxindeserto/voxindeserto.github.io/actions/workflows/hugo.yml/badge.svg)](https://github.com/voxindeserto/voxindeserto.github.io/actions/workflows/hugo.yml)

## 本機開發

### 環境需求

- Hugo Extended 0.167.0
- Go 1.25 或以上版本
- Dart Sass

首次啟動時，Hugo 會根據 `go.mod` 下載 Blowfish 主題。

```sh
hugo server
```

然後瀏覽 <http://localhost:1313/>。Hugo 會在檔案變更時自動重新載入網站。

## 新增或編輯內容

網站內容以 Markdown 撰寫。新增文章時，在 `content/blog/` 建立 Markdown 檔案，並於檔案開首加入標題、日期、摘要和標籤等 front matter。

| 路徑 | 用途 |
| --- | --- |
| `content/_index.md` | 首頁內容 |
| `content/biography.md` | 個人簡介 |
| `content/blog/` | 部落格文章 |
| `config/_default/` | Hugo、Blowfish、語言及導覽設定 |
| `assets/css/custom.css` | 網站自訂樣式 |
| `assets/img/`、`public/` | 網站圖片及其他靜態資源 |

## 部署

推送至 `main` 分支會自動觸發 GitHub Actions 建置並部署至 GitHub Pages。也可以在 [Deploy Hugo site to Pages 工作流程](https://github.com/voxindeserto/voxindeserto.github.io/actions/workflows/hugo.yml) 中選擇 **Run workflow** 手動部署。

上方的部署狀態按鈕可查看最近一次工作流程的結果，並連結至工作流程頁面。
