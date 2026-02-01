---
type: concept_note
aliases:
  - Discriminative AI
  - DAI
  - 鑑別式AI
topic:
  - "[[../0. MOCs/3. AI 知識 MOC#AI基礎知識]]"
source: 🤖 AI_generated
source_ref:
created: 2026-01-03
tags:
---
中文名稱：鑑別式AI
英文名稱：Discriminative AI
# 📌 定義（Definition）
鑑別式 AI 專注於學習數據特徵與目標標記之間的條件概率 P（y|x），主要用於分類與迴歸任務。

# ⭐原理與技術
鑑別式模型學的是**在給定輸入 x 的情況下，輸出 y 的機率**$$
P(y∣x)
$$
典型的鑑別式 AI 模型包括
-  [支援向量機](../AI知識/支持向量機(SVM).md)
- [邏輯迴歸（Logistic Regression）](../AI知識/邏輯迴歸（Logistic%20Regression）.md)
- [決策樹](../AI知識/決策樹.md)、[隨機森林](../AI知識/隨機森林(Random%20Forest）.md)
- 深度學習中的[深度神經網路](../AI知識/深度學習-深度神經網路.md)等。

## 與生成式 AI 的對照
- **鑑別式 AI**：學 P(y∣x)        
    - 用來判斷、分類、預測        
- **生成式 AI**：  學數據的聯合分佈 P(x,y) 或邊際分佈 P(x)        
    - 用來生成資料        

簡單對照： **鑑別式在「分」，生成式在「生」。**

# 🔗 應用領域



# 3 題模擬練習題