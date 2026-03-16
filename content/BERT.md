---
type: concept_note
aliases:
  - BERT
  - Bidirectional Encoder Representations from Transformers
topic:
  - "[[../0. MOCs/3. AI 知識 MOC#AI基礎知識]]"
source: 🤖 AI_generated
source_ref:
created: 2025-12-06
tags:
---
# BERT
中文名稱：BERT 預訓練模型
英文名稱：Bidirectional Encoder Representations from Transformers
# 定義（Definition）
基於 Transformer 編碼器的雙向預訓練語言模型，用遮罩填空（MLM）和句子關係判斷（NSP）學會上下文，再微調到各種 NLP 任務，常當作語意特徵骨架。
# 原理與技術
BERT 由多層 **Transformer Encoder** 堆疊，含 **多頭自注意力(Multi-head Self-Attention)**、殘差與 LayerNorm，能同時讀左右文。輸入含 **[CLS]、[SEP] 特殊符號**、**位置編碼(Position Embedding)** 與 **段落編碼(Segment Embedding)**，CLS 向量常拿來做句子級任務。預訓練的 **MLM(Masked Language Modeling)** 隨機遮罩 15% token，迫使模型用上下文猜字；**NSP(Next Sentence Prediction)** 判斷句子是否連續，幫助理解篇章關係（有些改成 SOP 或移除 NSP）。因為是雙向編碼，它比單向 LM 更適合理解與抽取；但它不是生成式模型。微調時通常加一個小型分類頭或 span 頭，需注意 **warmup、小學習率、梯度裁剪**，避免破壞預訓練特徵。長序列受 512 token 限制，可用 **滑窗切片** 或 **Longformer/DeBERTa** 等長上下文變體。效能優化可用 **參數高效微調([LoRA](../00.%20Inbox/LoRA%20低秩適應.md)/Prefix Tuning/Adapters)**、**模型蒸餾(DistilBERT)** 或 **量化(8-bit/4-bit)**。中文場景常用 **Whole Word Masking** 或結合 **詞彙/拼音特徵** 提升表徵。
# 應用領域
BERT 核心是產生高品質語意向量，常見用法：
- **文本分類**：情感、意圖、主題判斷，只需在 CLS 上接分類層。若類別不平衡，可調權重或用 focal loss。
- **序列標註**：命名實體識別、槽位填充、關鍵詞抽取，在每個 token 上接 CRF/分類頭，處理斷詞或混合語言時可加入詞典特徵。
- **問答與抽取**：閱讀理解、法律/醫療條文找答案 span，需控制輸入長度，長文可分段重排。
- **語意檢索/重排序**：句向量餵入向量資料庫；可用 **交叉編碼器(cross-encoder)** 做精排，**雙塔(bi-encoder)** 做粗排。
- **摘要與對話理解**：雖不生成，但可當 encoder 提取關鍵句再交給生成模型；也可做意圖檢測與安全審核。
- **領域微調**：金融、醫療、客服，可先做繼續預訓練(DAPT/TAPT)再下游微調，保留領域用詞。這些任務共同需求是「理解上下文與句間關係」，BERT 的雙向預訓練與可微調框架能在少量標註下快速上線。
# 3 題模擬練習題
1. BERT 的預訓練任務主要是哪兩個？
   - A. 自回歸語言模型 + 翻譯
   - **B. 遮罩語言模型(MLM) + 下一句判斷(NSP)**
   - C. 圖像分類 + 對比學習
   - D. 強化學習 + 文本生成
   - 正確答案：B
   - 解析：BERT 依靠 MLM 學上下文，NSP 學句間關係；其他選項不是預訓練核心。
2. 如果長度超過 512 tokens，最合理的處理方式是？
   - A. 直接截斷後半部
   - **B. 分段/滑窗或改用長序列變體（如 Longformer）**
   - C. 強制改用 RNN
   - D. 把所有字替換成 [MASK]
   - 正確答案：B
   - 解析：標準 BERT 長度限制 512，需分段或用長序列架構；直接截斷會喪失資訊。
3. 微調 BERT 時為何常用小學習率與 warmup？
   - A. 為了讓損失值更大
   - B. **避免破壞預訓練權重，平滑收斂**
   - C. 因為 GPU 記憶體不足
   - D. 為了跳過反向傳遞
   - 正確答案：B
   - 解析：預訓練權重已學到通用語意，小步調和 warmup 可防止梯度震盪導致災難性遷移。
