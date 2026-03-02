# Project Structure — FAANG Senior Standard

## 核心原則
依「功能」組織，不依「檔案類型」組織。

## 壞的結構（禁止）
src/
  components/
  hooks/
  utils/
  pages/

## 好的結構
src/
  features/          # 每個功能自成一個模組
    auth/
      components/
      hooks/
      api/
      types/
      index.ts       # 統一對外 export，外部只能從這裡引入
    dashboard/
  shared/            # 真正跨功能共用的才放這裡
    components/
    hooks/
    utils/
  app/               # 路由、全域設定、providers

## 規則
- 功能模組之間禁止互相引入，只能透過 shared
- 每個模組必須有 index.ts 作為唯一出口
- 型別定義放在模組內的 types.ts，不要全部集中在一個 global types 檔

## 命名規範
- 元件檔：PascalCase.tsx（UserCard.tsx）
- hook 檔：camelCase.ts（useUserProfile.ts）
- 工具函式：camelCase.ts（formatDate.ts）
- 常數：UPPER_SNAKE_CASE