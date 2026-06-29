# codefest.taipei (welcome)

codefest.taipei 首頁（歷屆活動入口），部署至 `codefest.taipei/welcome/`。

Firebase rewrites 設定根路徑 `**` 指向 `/welcome/index.html`，所以此站等同於網站首頁。

## 技術棧

- Nuxt 3（`ssr: false`，SPA 模式）
- Vue 3 + TypeScript
- Tailwind CSS
- i18n（`assets/locales/zh.json`）

## 開發

```bash
npm install
npx nuxi dev --port <port>
```

## 部署

本專案不直接部署，需透過 [codefest-deployment](https://github.com/Koafaith/codefest-deployment) repo 統一部署。

完整部署流程請參考 `codefest-deployment/CLAUDE.md`。

簡要流程：
1. 在本 repo 建立分支 → commit & push → PR → merge to main
2. 停掉 dev server
3. `npx nuxi generate && cp -r .output/public/* /path/to/codefest-deployment/public/welcome/`
4. 到 deployment repo 執行 `node addNonceToInlineScripts.js`
5. 部署到 demo 驗證 → 部署到 production

## Git 規範

- Commit 訊息格式：`feat: description` / `fix: description`，單行，不加 body
- 不直接 commit 到 main，一律走分支 → PR → merge
- PR body 不加 "Generated with Claude Code" 等 AI 標註

## 重要檔案

- `assets/locales/zh.json` — 活動列表、文案
- `nuxt.config.ts` — baseURL: `/welcome/`，SEO title 設定
- `pages/index.vue` — 首頁頁面
