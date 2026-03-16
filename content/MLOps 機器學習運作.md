---
type: concept_note
aliases:
  - 機器學習運作
  - Machine Learning Operations
  - MLOps
topic:
  - "[[../0. MOCs/3. AI 知識 MOC#AI基礎知識]]"
source: 🤖 AI_generated
source_ref:
created: 2026-03-16
tags:
---
中文名稱：機器學習運作
英文名稱：Machine Learning Operations
# 📌 定義（Definition）
**MLOps（Machine Learning Operations）** 是一套方法與流程，用來**讓機器學習模型可以穩定地被開發、部署、監控與持續更新**。可以理解為**把 DevOps 的概念，應用到 AI / Machine Learning。**


# ⭐原理與技術
## 典型流程
MLOps 的核心生命週期可以理解為：**問題定義 → 資料工程 → 模型開發 → 模型部署 → 模型監控 → 持續改進**。在這個流程中會涉及 Feature Store 管理特徵資料、Model Registry 管理模型版本、Batch 與 Online 推論模式、A/B Testing 與 Canary Deployment 的部署策略，以及 Data Drift 與 Concept Drift 的監控機制，再配合 CI/CD 自動化流程，形成一個可持續運作的 AI 系統管理架構。

### 1 問題定義與專案規劃（Problem Definition）

MLOps 的第一步是明確定義 AI 要解決的商業問題、評估資料是否足夠、設定模型評估指標與專案成功標準，同時也需要納入 **模型治理（Model Governance）** 的概念，例如模型責任歸屬、合規性、可解釋性與 AI 倫理問題，確保模型在企業環境中的使用符合規範並能被管理與追蹤。

|類型|說明|
|---|---|
|模型偏見|Bias|
|法規遵循|Compliance|
|可解釋性|Explainability|
### 2 資料管理與資料工程（Data Engineering）

在資料工程階段需要建立資料蒐集、清理、標註與 [[特徵工程]]流程，同時管理資料版本與資料品質。此階段通常會建立 **Feature Store** 來集中管理模型使用的**特徵資料**，使不同模型可以重複使用相同特徵，避免重複特徵工程並維持訓練與推論的一致性。資料版本與程式碼版本通常透過 Git 或資料版本工具進行管理，確保模型訓練過程可以被追溯與重現。

**版本控制（Version Control）**

MLOps 中需要管理三種版本：

| 類型            | 說明   | 工具     |
| ------------- | ---- | ------ |
| Code version  | 程式碼  | Git    |
| Data version  | 資料版本 | DVC    |
| Model version | 模型版本 | MLflow |

### 3 模型開發與訓練（Model Development）

模型開發階段由資料科學家進行模型選擇、特徵工程、模型訓練與模型評估，並透過[各種評估指標](損失函數（Loss%20Function）.md#常見的損失函數包括%20：)（例如 Accuracy、Precision、Recall、RMSE 等）判斷模型效果。訓練完成後，模型會被存放到 **Model Registry** 進行版本管理，Model Registry 會追蹤模型版本、訓練資料與模型指標，並作為未來部署與回滾模型的重要依據。

**Model Registry** 是一個用來**集中管理機器學習模型版本與生命週期的系統或儲存庫**。在 MLOps 流程中，每當模型訓練完成，就會將模型及其相關資訊（例如訓練資料版本、模型參數、評估指標與部署狀態）登錄到 Model Registry，使團隊能夠追蹤模型歷史、比較不同模型版本並控制部署。Model Registry 的核心功能通常包括模型版本管理、模型狀態管理（例如「開發中」「測試中」「生產環境」）、部署與回滾控制以及模型審核與治理。實務上，如果沒有 Model Registry，企業很容易出現「不知道目前系統用的是哪個模型版本」或「模型更新後無法回退」的問題，因此 Model Registry 被視為 MLOps 的核心基礎設施之一。常見實作工具包括 MLflow Model Registry、Kubeflow Model Registry 或雲端平台的模型管理服務。

### 4 模型部署（Model Deployment）

模型完成後需要部署到實際系統中提供推論服務。部署模式主要分為 **批次推論（Batch Inference）** 與 **線上／即時推論（Online / Real-time Inference）**，前者通常用於定期大量預測（例如每日需求預測），後者則透過 API 即時回應使用者請求（例如推薦系統或聊天機器人）。在模型部署過程中，企業常會使用 **Canary Deployment** 逐步釋出新模型，先讓少量流量使用新模型以降低風險，同時也會透過 **A/B Testing** 比較新舊模型在實際環境中的效果。

**Canary(金絲雀) Deployment** 是一種**逐步部署新模型或新系統版本的策略**，其做法是先讓一小部分使用者或流量使用新模型，並持續監控系統效能與預測品質，如果沒有問題，再逐步擴大使用比例直到完全取代舊版本。這種方式之所以稱為「Canary」，源自早期礦工在礦坑中使用金絲雀偵測有毒氣體的做法；在軟體與 AI 系統中，新版本模型就像金絲雀一樣，先在小範圍環境測試是否安全。Canary Deployment 的主要優點是能夠降低部署風險、快速發現問題並在必要時立即回退到舊模型，因此在 AI 系統更新、推薦系統調整或風險控制模型部署中非常常見。與一次性全面部署相比，Canary Deployment 可以在實際環境中驗證模型效果，同時避免大規模系統故障。

### 5 模型監控與管理（Model Monitoring）

模型部署後需要持續監控模型效能、系統延遲與預測品質，同時追蹤資料與模型行為的變化。監控重點包括 **資料飄移（Data Drift）** 與 **概念飄移（Concept Drift）**，前者代表輸入資料的分布改變，後者代表問題本身的規則改變，兩者都可能導致模型準確度下降，因此需要**透過監控機制及早發現問題並觸發重新訓練流程**。

| 類型            | 改變的是             | 主要原因      | 例如     | 解決方式        |
| ------------- | ---------------- | --------- | ------ | ----------- |
| Data Drift    | 資料分布             | 環境或族群變化   | 新產品資料  | 重新蒐集資料並重新訓練 |
| Concept Drift | 問題規則<br>輸入與標籤的關係 | 規則或行為模式改變 | 詐騙模式改變 | 更新模型或重新定義問題 |

### 6 持續改進與自動化（Continuous Improvement）

MLOps 的最後階段是建立自動化流程，使模型可以隨資料變化持續更新。這通常透過 **自動化與 CI/CD（Continuous Integration / Continuous Deployment）** 或 Continuous Training 來完成，當資料更新或模型效能下降時，系統可以自動重新訓練模型、進行測試並部署新版本，使整個 AI 系統形成「資料更新 → 模型訓練 → 模型部署 → 模型監控 → 再訓練」的持續循環。

常見工具：

- Kubeflow    
- Airflow    
- Jenkins
# 🔗 應用領域



# 3 題模擬練習題

**題型 1**

MLOps 的主要目的為何？

A 提高 GPU 效率  
B 管理 AI 模型生命週期  
C 提升資料庫速度

答案：

**B**

---

**題型 2**

下列哪一項不是 MLOps 重點？

A 資料管理  
B 模型監控  
C UI 設計

答案：

**C**