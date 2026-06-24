# 學生憂鬱症風險預測之機器學習模型評估與可解釋性分析
> **An Evaluative Study of Predictive Modeling and Explainable AI for Student Depression Risk Assessment**

本專案為大專院校資訊管理學系之畢業專案核心技術成果。現代社會與校園群體中的心理健康議題日益嚴峻，本研究旨在透過資料科學與機器學習方法，針對高達 27,902 筆學生生活型態、學業壓力及心理評估數據進行深度建模。透過建構高準確度的二元分類模型，本專案期望能為校園輔導諮商、早期預警系統及臨床決策支援提供具備統計學顯著性的實證依據。

---

## 🚀 核心亮點與個人技術貢獻
本專案由 9 位組員共同協作，本人於團隊中擔任**技術核心成員（Core Technical Lead）**，獨立負責並主導以下資料科學 Pipeline 的完整實作：

* **強健型資料前處理 (Robust Data Preprocessing)**
  * 面對 27,902 筆龐雜且包含噪訊的原始數據，執行了嚴謹的資料清洗與缺失值處理。
  * 針對數值特徵，採用 `RobustScaler` 進行強健型特徵縮放，有效阻絕極端異常值（Outliers）對機器學習模型訓練的干擾[cite: 2]。
  * 針對類別變數，使用 `OneHotEncoder` 進行獨熱編碼，確保底層演算法能精準捕捉非線性特徵關係[cite: 2]。

* **嚴謹實驗防錯機制 (Anti-Overfitting Design)**
  * 為了防範資料分割時產生類別不平衡的偏差，主導採用 8:2 比例搭配**分層抽樣（Stratified Sampling）**切分訓練集與測試集[cite: 2]。
  * 在模型訓練階段全面導入 **五折分層交叉驗證（Five-Fold Stratified Cross-Validation）**[cite: 2]，確保模型具備高度的泛化能力與穩定性，消弭過擬合（Overfitting）風險。

* **自動化超參數調校 (Automated Hyperparameter Optimization)**
  * 建構、評估並橫向對比了五種主流機器學習演算法[cite: 2]：邏輯迴歸（LR）、隨機森林（RF）、極限梯度提升（XGBoost）、支援向量機（SVM）與 K 最近鄰居（KNN）。
  * 獨立運用 `RandomizedSearchCV` 結合交叉驗證進行大範圍的超參數精細調校，成功逼近各模型的預測效能極限[cite: 2]。

* **可解釋性 AI 應用 (Explainable AI & Feature Importance)**
  * 拒絕傳統機器學習的「黑箱盲點」，透過**特徵重要性分析（Feature Importance Analysis）**透視模型決策邏輯[cite: 2]。
  * 成功追溯出「學業壓力（Academic Pressure）」與「自殺念頭（Suicidal Thoughts）」為影響憂鬱症預測的最核心風險因子，使數據成果具備實務臨床解釋力[cite: 2]。

---

## 📊 實驗結果與效能評估

在全面的多維度效能評估中（涵蓋 Accuracy, Precision, Recall, F1-score, AUROC 與 AUPRC）[cite: 2]，經過參數優化後的模型均表現優異。其中以**邏輯迴歸**與 **XGBoost** 在分類能力上最為傑出[cite: 2]：

| 評估模型 (Models) | 交叉驗證 AUROC (CV AUROC) | 核心特徵重要性 (Key Features) |
| :--- | :---: | :--- |
| **Logistic Regression (LR)** | **0.922** | 學業壓力 (Academic Pressure)、自殺念頭 (Suicidal Thoughts)[cite: 2] |
| **Extreme Gradient Boosting (XGBoost)** | **0.921** | 睡眠品質 (Sleep Quality)、工作/學習壓力[cite: 2] |
| Random Forest (RF) | 0.915 | 社交互動頻率、生活型態變數[cite: 2] |

> **研究洞察**：實驗結果強烈驗證了機器學習方法在心理健康風險篩檢上的高度可行性[cite: 2]。本系統不僅追求頂級的預測準確率，更強調「可解釋性」，能將數據洞察直接轉化為學校輔導單位的防範方針，具備極高的決策支援價值[cite: 2]。

---

## 🛠️ 開發環境與技術棧
* **開發語言**: Python 3.x[cite: 2]
* **核心庫與框架**:
  * **資料處理/工程**: `pandas`, `numpy`, `scikit-learn`[cite: 2]
  * **梯度提升框架**: `xgboost`[cite: 2]
  * **數據視覺化**: `matplotlib`, `seaborn`

---

## 📦 如何在本地端重現本專案

1. **複製專案倉庫 (Clone Repository)**
```bash
   git clone [https://github.com/你的GitHub帳號/student-depression-prediction-ml.git](https://github.com/你的GitHub帳號/student-depression-prediction-ml.git)
   cd student-depression-prediction-ml
建立虛擬環境與安裝依賴套件 (Environment Setup)

Bash
   python -bin venv venv
   source venv/bin/activate  # Windows 環境請執行: venv\Scripts\activate
   pip install -r requirements.txt
執行模型訓練與評估 (Run Interactive Notebook)
進入 notebooks/ 目錄並啟動 Jupyter Notebook，開啟 depression_risk_modeling.ipynb。你可以完整重現資料清洗、特徵強健型縮放、模型比對、超參數自動化調校以及最終特徵重要性視覺化圖表的完整實驗流水線[cite: 2]。

👥 團隊與指導致謝
指導教授：陳澤雄 博士[cite: 2]

團隊協作：本專案由 9 位組員共同協作完成[cite: 2]。本人作為技術核心，主導了特徵工程、模型建立、防過擬合實驗設計、參數調優及效能評估等關鍵模組開發[cite: 2]。特別感謝陳澤雄教授在模型可解釋性與學術嚴謹度上的指導，使本專案得以圓滿發表[cite: 2]。
