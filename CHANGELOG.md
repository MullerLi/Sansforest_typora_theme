# Sansforest Typora Theme - Development Log

## 2026-04-02: Typography & Structure Optimization

本次版更著重於閱讀體驗的字體管理優化、假粗體 (Faux Bold) 錯誤的修正，以及 Markdown 樣式的整體比例對齊。

### 1. Typography (字體設定優化)
* **取消 `font-weight` 自動判定機制**：
  為避免 Typora (Chromium 引擎) 在中文自定義字體下，因找不到正確粗細而渲染出模糊的「偽粗體」，本次更新徹底移除了 `@font-face` 以及 CSS 標籤內的 `font-weight: 500/700` 設定。
  改為**為各個字重建立專屬的 font-family 名稱** (例如 `"Blix SemiBold"`, `"Heading Mixed Medium"`)，並以 `font-weight: normal` 強制精準綁定相對應的 `.otf` / `.ttf` 字體檔案。
* **源流明體更新**：
  內文的中文字體從 `GenRyuMin M` 改為使用 `GenRyuMin L` 以提供更清晰且舒適的長文閱讀感受。
* **襯線英文字型抽換**：
  全面將內文原有的英文襯線字體 `Lora` 替換為 `Libre Baskerville`。完成對應套用在 `em`, `i` 斜體設定以及 `--font-serif-latin` 中。

### 2. Consistency & Layout (排版一致性修正)
* **清單粗細修正**：
  移除了無次序清單 (`ul`) 與次序清單 (`ol`) 異常套用 `Medium` 中粗體的強制覆寫設定，使其與 `p` 段落一樣自然繼承 `Regular`。
* **字體大小比例調校**：
  在主體內文 (`p`, `li`) 維持易讀大小 `1.25rem` 的前提下，同步調升了原本偏小的 Markdown 元素：
  * **表格 (`table`)**：由 `1rem` 放大至 `1.15rem`，解決過去表格字體比正文小 20% 的狀況。
  * **行內程式碼與區塊 (`code`, `pre`)**：由 `0.95rem` 微幅提升至 `1.05rem`，使其與中文字型的視覺寬度更加相容。
  * **最小標題 (`h6`)**：原本為 `1.1rem`，上調至 `1.2rem` 並維持全大寫，藉由些微的高度縮減區隔本文，但不再出現標題比內文還小的視覺違和感。

### 3. File Cleanup (檔案整理)
* 將原有的 `Lora` 系列檔案以及在新增過程中產生的一些疊代、冗餘檔案 (如 `*_2.ttf`)，全數移至備份區 `oldversion/unused_fonts/`，保持 `sansforest` 核心資源包的乾淨、精簡。
