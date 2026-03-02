# Code Style — FAANG Senior Standard

## 通用原則
- 單一職責：一個函式 / 元件只做一件事
- 命名要能自我說明，禁止 a、b、temp、data 這類無意義命名
- 避免超過 3 層的巢狀邏輯，用 early return 扁平化
- Magic number 必須抽成命名常數
- 非同步一律用 async/await，禁止 callback hell

## React
- 優先使用 functional component + hooks
- 自訂 hook 前綴必須是 use，且只處理單一關注點
- props 必須有明確型別（TypeScript interface 或 PropTypes）
- 避免在 JSX 裡寫複雜邏輯，抽成變數或函式

## Vue
- Composition API 優先（Vue 3）
- 用 defineProps / defineEmits 明確宣告介面
- 複雜邏輯抽成 composable（useXxx.ts）

## Angular
- 嚴格遵守 OnPush change detection strategy
- Service 負責資料邏輯，Component 只負責 UI
- 善用 RxJS，避免手動 subscribe 忘記 unsubscribe

## TypeScript（所有框架）
- 禁止 any，用 unknown + type guard 替代
- 善用 utility types（Partial、Pick、Omit）
- API response 必須定義 interface，不可直接用