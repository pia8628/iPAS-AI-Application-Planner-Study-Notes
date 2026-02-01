---
type: concept_note
aliases:
  - Transformer
  - Transformer Architecture
topic:
  - "[[../0. MOCs/3. AI 知識 MOC#AI基礎知識]]"
source: 🤖 AI_generated
source_ref:
created: 2025-12-06
tags:
---

中文名稱：Transformer 架構
英文名稱：Transformer Architecture
# 定義（Definition）
Transformer 是一種用「注意力」機制來處理序列資料的模型，不用循環或卷積，能同時看到整個序列，速度快且效果好，廣泛用在語言和影像等 AI 領域。
# 原理與技術

## 架構
Transformer 由 **編碼器(Encoder)** 與 **解碼器(Decoder)** 堆疊的多層 Block 組成（純 Encoder 用於 BERT，純 Decoder 用於 GPT）。
單層包含：
- **多頭自注意力(Multi-head Self-Attention)**：模型會同時從多個角度看序列中各個位置的關係，幫助理解遠距離的依賴。
- **殘差連接與正規化**：讓模型學習更穩定。每個子層後有殘差連接與 LayerNorm，穩定梯度。
- **前饋網路(FFN)**：簡單的多層全連接層，提升表現力。
- **位置編碼(Positional Encoding/Embedding)**：告訴模型序列中每個元素的位置，因為注意力本身不在乎順序。
- **解碼器用遮罩自注意力**，確保生成文字時只能看到已生成的詞，避免作弊。

## 為什麼 Transformer 比 RNN 快？  
因為 Transformer 可以同時處理整個序列，不用一個一個時間步慢慢算。

# 應用領域
- **語言建模與生成**：GPT 系列聊天、摘要、翻譯、程式生成；需要長上下文則用長序列注意力。
- **理解任務**：BERT/DeBERTa 用於分類、問答、檢索重排序。
- **機器翻譯**：原始 Transformer 架構即為翻譯設計，Encoder-Decoder 直接對齊源與目標句。
- **推薦與時間序列**：用注意力捕捉用戶行為序列或市場序列的遠距關係。
- **電腦視覺**：ViT、Swin Transformer 做分類、檢測、分割；可結合 CNN 抓局部細節。
- **多模態與語音**：CLIP、Vision-Language、語音-文字模型皆以注意力融合不同模態。
共通重點：注意力計算成本與序列長度平方成長，需挑選合適的長序列或稀疏策略；訓練需充足資料與正規化，推論可用量化與快取減少延遲。
# 3 題模擬練習題
1. Transformer 為何比 RNN 更易並行？
   - A. 因為參數更少
   - **B. 自注意力可同時處理整個序列，不需逐步傳遞狀態**
   - C. 只用 CPU
   - D. 沒有激活函數
   - 正確答案：B；解析：RNN 需一步步算，Transformer 一次算所有位置，並行度高。
2. 解碼器中的「遮罩自注意力」作用？
   - A. 提高學習率
   - **B. 確保模型只看見前面 token，維持因果生成**
   - C. 讓模型看未來詞
   - D. 壓縮模型大小
   - 正確答案：B；解析：遮罩阻止模型偷看未來，避免訓練時資訊洩漏。

