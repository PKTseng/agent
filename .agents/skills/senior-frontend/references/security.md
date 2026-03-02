# Security — FAANG Senior Standard

## XSS 防禦
- 禁止使用 innerHTML、dangerouslySetInnerHTML（除非內容來源可完全信任且已 sanitize）
- 如果必須渲染 HTML，使用 DOMPurify 做 sanitize
- 用戶輸入在顯示前必須 escape

## CSRF
- 非 GET 請求必須帶 CSRF token
- 不依賴 cookie 做身份驗證的唯一依據

## 敏感資料
- 禁止在前端 log 出 token、密碼、個資
- localStorage 不存 JWT 或敏感 token（用 httpOnly cookie）
- .env 變數只放可公開的設定，VITE_/NEXT_PUBLIC_ 前綴的都會暴露給客戶端

## 第三方套件
- 定期執行 npm audit
- 不引入超過 1 年沒有維護的套件做核心功能

## CSP（Content Security Policy）
- 新專案必須設定 CSP header
- 禁止 unsafe-inline，改用 nonce 或 hash

## API 通訊
- 所有 API 請求強制走 HTTPS
- 不在 URL query string 放敏感參數（會被 server log 記錄）