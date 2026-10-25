# 荒野中的呼喊者

以繁體中文記錄生活與想法的個人網站，使用 [Hugo](https://gohugo.io/) 和 [Blowfish](https://blowfish.page/) 建置，並透過 GitHub Pages 託管。

[![部署至 GitHub Pages](https://github.com/voxindeserto/voxindeserto.github.io/actions/workflows/hugo.yml/badge.svg)](https://github.com/voxindeserto/voxindeserto.github.io/actions/workflows/hugo.yml)
[![部署至 GitLab](https://img.shields.io/badge/Deploy%20to-GitLab-fc6d26?logo=gitlab&logoColor=white)](https://gitlab.com/projects/new#import_project)
[![部署至 Vercel](https://img.shields.io/badge/Deploy%20to-Vercel-black?logo=vercel&logoColor=white)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fvoxindeserto%2Fvoxindeserto.github.io)
[![部署至 Netlify](https://img.shields.io/badge/Deploy%20to-Netlify-00c7b7?logo=netlify&logoColor=white)](https://app.netlify.com/start/deploy?repository=https%3A%2F%2Fgithub.com%2Fvoxindeserto%2Fvoxindeserto.github.io)

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

### GitLab Pages

在 GitLab 專案根目錄新增 `.gitlab-ci.yml`，使用包含 Hugo Extended 0.167.0、Go 1.25 和 Dart Sass 的 runner 映像建置網站，並將 `out/` 設為 Pages 發佈目錄。以下範例使用 HugoMods 的 Hugo 映像：

```yaml
image: hugomods/hugo:exts-0.167.0

pages:
  script:
    - hugo --minify --baseURL "${CI_PAGES_URL%/}/"
  pages:
    publish: out
  rules:
    - if: $CI_COMMIT_BRANCH == $CI_DEFAULT_BRANCH
```

將 `.gitlab-ci.yml` 推送至預設分支後，GitLab CI/CD 會建置並發佈網站；可在專案的 **Deploy > Pages** 查看網址和部署狀態。

### Vercel

將 Git 儲存庫匯入 Vercel，Framework Preset 選 **Hugo**，並設定：

| 設定 | 值 |
| --- | --- |
| Build Command | `hugo --minify` |
| Output Directory | `out` |
| Hugo 版本 | `0.167.0` |
| Go 版本 | `1.25` |

確保建置環境也提供 Dart Sass。之後每次推送至已連結的分支，Vercel 都會自動建置及部署。

### Netlify

將 Git 儲存庫連結至 Netlify，或在專案根目錄新增 `netlify.toml`：

```toml
[build]
  command = "hugo --minify"
  publish = "out"

[build.environment]
  HUGO_VERSION = "0.167.0"
  GO_VERSION = "1.25.0"
  HUGO_ENVIRONMENT = "production"
```

確保 Netlify 建置環境也提供 Dart Sass。連結儲存庫後，Netlify 會在推送時自動重新建置與部署。

> Hugo 設定中的 `baseURL` 目前指向 GitHub Pages 網址。若改用其他平台作為正式網站，請將它更新為該網站的正式網址，或在建置命令中以 `--baseURL` 指定，確保網站連結和 sitemap 使用正確網址。
