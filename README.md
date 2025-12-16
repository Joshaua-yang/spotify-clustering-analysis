# Spotify Music Clustering Analysis 🎵

## 專案簡介 (Project Overview)
本專案使用非監督式學習 (Unsupervised Learning) 技術，針對 Spotify 資料庫中超過 **120 萬筆** 歌曲進行分析。目標是透過音訊特徵 (Audio Features) 自動識別音樂風格流派，並探索 K-Means 與 Gaussian Mixture Models (GMM) 在處理大規模音樂資料時的差異。

## 核心技術 (Tech Stack)
- **語言**: Python 3.12
- **資料處理**: Pandas, NumPy
- **機器學習**: Scikit-learn (K-Means, GMM)
- **視覺化**: Matplotlib, Seaborn, UMAP (降維分析)

## 分析流程 (Workflow)
1. **資料前處理**: 
   - 特徵標準化 (StandardScaler)。
   - 處理 1.2M 筆大規模資料。
2. **最佳 K 值探索**: 
   - 結合 Silhouette Coefficient 與 CH Index 指標。
   - 使用 UMAP 進行降維視覺化驗證，最終選定 **k=7**。
3. **模型訓練**:
   - **K-Means**: 作為基準模型 (幾何距離切分)。
   - **GMM**: 作為對照組 (機率分佈切分)，捕捉曲風過渡地帶。
4. **群組畫像 (Cluster Profiling)**: 定義七大聽感群組。

## 主要發現 (Cluster Insights)
透過數據輪廓分析，我們將歌曲自動切分為以下七大類：

| Cluster ID | 代表風格 | 特徵描述 |
| :--- | :--- | :--- |
| **Cluster 0** | **Hip-Hop / Rap** | 高語音感 (Speechiness) 與高髒標率 (Explicit)。 |
| **Cluster 1** | **Live Performance** | 異常突出的現場感 (Liveness)。 |
| **Cluster 2** | **Happy Pop / Dance** | 高情緒正向度 (Valence) 與舞曲感，適合派對。 |
| **Cluster 3** | **Classical / Ambient** | 極低能量、高器樂感，屬於古典或療癒純音樂。 |
| **Cluster 4** | **Acoustic / Folk** | 高原聲感但含人聲，屬於不插電或民謠抒情。 |
| **Cluster 5** | **EDM / Trance** | 高器樂感且高能量，屬於電子舞曲。 |
| **Cluster 6** | **Rock / Metal** | 極致的高能量 (Energy) 與快節奏 (High BPM)。 |

## 結論 (Conclusion)
本專案發現音樂資料呈現連續的「大陸塊」分佈，而非離散聚落。
- **K-Means** 提供了穩健的基礎分類。
- **GMM** 則揭示了 K-Means 無法捕捉的細節（例如將古典樂拆分得更細，或重新分配模糊的抒情歌），證明了音樂風格具有漸進、混合的本質。這為實現「基於情境 (Context-based)」的精準推薦系統提供了強有力的數據支持。

---
*License: MIT*