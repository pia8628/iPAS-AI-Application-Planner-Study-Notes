---
type: concept_note
aliases:
  - Stable Diffusion
  - Latent Diffusion
  - SD
topic:
  - "[[../0. MOCs/3. AI 知識 MOC#AI基礎知識]]"
source: 🤖 AI_generated
source_ref:
created: 2025-12-06
tags:
---
# Stable Diffusion
中文名稱：穩定擴散（潛變分散模型）
英文名稱：Stable Diffusion / Latent Diffusion
# 定義（Definition）
一種生成式影像模型，先把圖片壓到潛在空間，再用擴散過程逐步去噪並受文字控制，能在家用顯卡上生成高品質圖片，廣泛用於繪圖與設計。
# 原理與技術
核心是 **潛空間擴散(Latent Diffusion)**：先用 **自編碼器(VAE)** 把高維圖片壓縮成潛向量 z，擴散只在潛空間運作，計算成本更低。訓練時加入高斯噪聲，多步生成 **噪聲預測模型**（通常是 **U-Net** 搭配 **殘差與注意力**）去預測並移除噪聲；反覆迭代即可把雜訊還原成圖。文字控制透過 **CLIP/文本編碼器** 產生條件向量，進入 **交叉注意力(Cross-Attention)** 引導生成內容。常見取樣器有 DDIM、Euler、DPM++ 等，步數影響速度與品質。為適配個人化，會做 **LoRA/文本反轉(Textual Inversion)/DreamBooth** 微調，小規模即可把特定風格或角色融入。安全層面可加入 **NSFW 過濾、版權提醒**，並限制上傳資料。推論時可調 **CFG scale** 控制文本遵從度，調 **種子** 保持可重現。影像控制可用 **ControlNet**（邊緣、姿勢、深度）、**Inpainting/Outpainting** 修圖、或 **Image-to-Image** 變換。

![VAE vs GAN vs Diffusion（簡單比較表）](生成式人工智慧(Gen%20AI).md#VAE%20vs%20GAN%20vs%20Diffusion（簡單比較表）)
# 應用領域
- **插畫與概念設計**：快速出草稿，提供多版本風格。可在遊戲、影視前期做分鏡與場景氛圍圖。
- **產品與廣告視覺**：生成背景、氛圍、道具，減少拍攝成本，並可用 inpainting 修改局部。
- **照片修復與增強**：舊照上色、去除雜物、超解析度；結合 ControlNet 控制構圖。
- **角色/風格定製**：以 LoRA/DreamBooth 讓模型記住品牌角色或特定畫風，保障一致性。
- **教育與研究**：視覺化抽象概念、創意發想、學習生成式模型原理；也能做資料增強。
- **醫療/工業影像生成（需審慎）**：用於模擬或增強，需避免偽造真實醫療資訊並經過審核。
共通重點：控制性與安全性很重要，要設定輸入審核、輸出過濾與記錄；商業使用需確認版權、訓練資料來源與品牌一致性。
# 3 題模擬練習題
1. Stable Diffusion 為何能在家用顯卡運行？
   - A. 因為不用 GPU
   - **B. 在潛在空間運行擴散，特徵圖更小、計算量低**
   - C. 完全不需要模型
   - D. 只生成黑白
   - 正確答案：B；解析：Latent Diffusion 把影像壓縮後再去噪，省記憶體與計算。
2. 文字如何影響生成內容？
   - A. 靠隨機種子
   - **B. 透過文本編碼器與交叉注意力控制 U-Net**
   - C. 把文字直接拼在圖片上
   - D. 只能改色彩
   - 正確答案：B；解析：CLIP 向量進入 Cross-Attention，引導每步去噪方向。
3. 想讓模型記住特定角色，常用？
   - A. 更換取樣器
   - B. **LoRA 或 DreamBooth 微調**
   - C. 增加 CFG scale 到無限
   - D. 只調整種子
   - 正確答案：B；解析：小樣本微調能注入新概念，其他操作無法固定新角色。
