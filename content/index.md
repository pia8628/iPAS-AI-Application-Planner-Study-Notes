# 人工智慧基本概念
## 快速索引
- [索引：AI 基礎與治理](索引-基礎與治理.md)
- [索引：資料處理與分析](索引-資料處理與分析.md)
- [索引：機器學習與深度學習](索引-機器學習與深度學習.md)
- [索引：生成式 AI 與導入](索引-生成式AI與導入.md)

## AI 基礎概論
### AI 發展
- [專家系統](專家系統.md) 1950-1980
- 機器學習時代 1980-2010
- 深度學習大數據 2010-
- 生成式 AI 與大模型時代 2020-
  (ChatGPT 於 2022 年 11 月向公眾推出)
### AI 治理
- AI 定義
- AI 類型
	- [弱人工智慧(Narrow AI-Weak AI)](弱人工智慧(Narrow%20AI-Weak%20AI).md)
	- [強人工智慧(General AI-Strong AI)](強人工智慧(General%20AI-Strong%20AI).md)
	- [超人工智慧 (Super AI-Super Intelligence)](超人工智慧%20(Super%20AI-Super%20Intelligence).md)
- 依技術分類
	- [符號式AI (Symbolic AI)](符號式AI%20(Symbolic%20AI).md)
	- [機器學習 (Machine Learning)](機器學習%20(Machine%20Learning).md)
	- [深度學習](深度學習-深度神經網路.md)
### AI 法規
- 負責任的 A（Resiponsible AI，RAI）
	- 公平&無偏見
	- 透明&可解釋性
	- 安全&穩健性
	- 責任與治理
- 台灣 AI 
	- 台灣人工智慧法草案
	- 行政院及所屬機關 (構) 使用生成式 AI 參考指引
	- 金管會-金融業運用人工智慧指引
- [歐盟人工智慧法案](歐盟人工智慧法案(EU%20AI%20Act).md)
- [人在AI決策系統中的角色](人在AI決策系統中的角色.md) HIC、HITL、HOTL
## 資料處理分析概論
### 資料基礎
- 統計基本
	- 中央趨勢：平均數（Mean）、中位數（Median）和眾數（Mode）
	- 分散度之衡量：四分位數（Quartile）、全距（Range）、四分位距（Interquartile Range, IQR）、平均差（Mean Deviation）、變異數（Coefficient of Variation）及標準差（Standard Deviation）等
- 資料類型
	- 結構化資料 Structured Data，如 SQL
	- 半結構化資料 Semi-structured Data，如 CSV, JSON, XML (用於 API 傳輸)
	- 非結構化資料 Unstructured Data，需要透過 [NLP](../00.%20Inbox/自然語言處理（Natural%20Language%20Process)、[CV](電腦視覺（Computer%20Vision）.md) 、語音辨識等 AI 技術處理
- 資料型態
	- 文字型
	- 數字型
	- 日期/時間型
	- 布林值
### 資料前處理
- 資料蒐集
- [資料清洗](數據清洗.md)
- [資料轉換](數據轉換.md)
- 資料統一 (Data Intergration/Unification)
	- 跨來源合併
	- 格式與單位統一
	- 主鍵/代碼標準化：唯一識別碼 ID
- 資料探勘
### 資料分析
- [探索性分析EDA](探索性分析.md)
- [驗證性資料分析CDA](驗證性分析（Confirmatory%20Data%20Analysis）.md)
- [診斷性分析（Diagnostic Analysis）](診斷性分析（Diagnostic%20Analysis）.md)
- [[預測性分析（Predictive Analysis）]]
- 視覺化圖表
- 大數據
### 資料隱私與安全
- 資料隱私
- 資料安全

## 機器學習概論
### 機器學習
[[機器學習 (Machine Learning)]]
- 學習模型
- 模型訓練與效能評估
- [過擬合](過擬合（Overfitting）.md)、[欠擬合](欠擬合（Underfitting）.md)
- 調校與優化
### 深度學習
[[深度學習-深度神經網路|深度學習]]
- 學習模型
- 前向與反向傳播
- [梯度下降法（Gradient Descent）](梯度下降法（Gradient%20Descent）.md)
- [激活函數](深度學習-深度神經網路.md#^6cfb67)

### 電腦視覺
- CV 技術
- CV 應用

## 生成式 AI 概論
### 鑑別式 AI
- [鑑別式AI（Discriminative AI）](鑑別式AI（Discriminative%20AI）.md)
- [支援向量機](支持向量機(SVM).md)
- [羅吉斯回歸](邏輯迴歸（Logistic%20Regression）.md)
- [決策樹](決策樹.md)、[隨機森林](隨機森林(Random%20Forest）.md)
### 生成式 AI
- [生成式人工智慧(Gen AI)](生成式人工智慧(Gen%20AI).md)
- [生成對抗網路(GAN)](生成對抗網路（Generative%20Adversarial%20Networks）.md) 逐漸被 Diffusion 取代
- [變分自編碼器VAE](變分自編碼器VAE.md)
- [擴散模型Diffusion](Stable%20Diffusion.md)
- [Transformer](Transformer架構.md) (GPT、Gemini、DALL. E 都屬此架構)
- 流式模型（Flow-based Generative Model）

# 生成式 AI 應用與規劃
## No code / Low code
- [No code](No%20code.md)
- [Low code](Low%20code.md)
- GenAI 結合 No/low code，提供建議、生成程式碼
- [No Code、 Low Code 平台選擇與評估](No%20Code、%20Low%20Code%20平台選擇與評估.md)
- [No Code、 Low Code 風險](No%20Code、%20Low%20Code%20風險.md)
- 優點：降低開發成本、縮短上市時間、加速數位轉型
- [AI民主化](AI民主化.md)

## GenAI 應用
- [AI 即服務（AIaaS）](AI%20即服務（AIaaS）.md)

## 導入 GenAI 評估規劃
- [生成式AI導入評估](生成式AI導入評估.md)
- [生成式AI導入規劃](生成式AI導入規劃.md)
- 生成式 AI 風險管理
