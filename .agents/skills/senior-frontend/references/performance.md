# Performance — FAANG Senior Standard

## Code Splitting
- 路由層級一定要 lazy load
- 非首屏元件用動態 import
- 第三方套件評估是否有更輕量的替代方案

## React 效能
- useMemo：用在計算成本高的純函式結果
- useCallback：用在傳給子元件的函式（避免不必要 re-render）
- React.memo：用在 props 變化頻率低的子元件
- 禁止在 render 裡直接建立物件 / 陣列作為 props（每次都是新 reference）

## Vue 效能
- 大型列表用 v-memo 或虛擬滾動（vue-virtual-scroller）
- computed 替代 methods 處理衍生資料
- 避免 watch 做過多事情，拆細或改用 watchEffect

## 圖片與資源
- 圖片一律用 WebP + 提供 fallback
- 重要圖片加 fetchpriority="high"，非關鍵圖片加 loading="lazy"
- 字型用 font-display: swap

## 網路
- API 請求做 deduplication（同一時間不發兩次相同請求）
- 適當使用 stale-while-revalidate 快取策略
- 大量資料考慮分頁或無限滾動，禁止一次載入全部