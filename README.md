# 機器學習技術應用於憂鬱症風險預測之模型評估
> **An Evaluation of Machine Learning Models for Student Depression Risk Prediction**

本專案為大專院校資管系之畢業專案成果。因應現代社會心理健康議題日益受到重視，本研究旨在透過機器學習方法，針對巨量學生生活型態與心理評估數據進行二元分類建模，建立高準確度的憂鬱症風險預測模型，期望能為校園輔導諮商及臨床決策支援提供具備統計學顯著性的實證依據。

## 🚀 核心亮點與個人貢獻
* **強健型資料前處理 (Data Preprocessing)**：針對高達 27,902 筆的複雜原始數據進行完整的資料清洗與缺失值處理。採用 `RobustScaler` 進行強健型特徵縮放，有效降低極端異常值對模型訓練的干擾；並使用 `OneHotEncoder` 處理類別變數。
* **嚴謹實驗防錯機制**：採用 8:2 比例搭配**分層抽樣 (Stratified Sampling)** 劃分訓練與測試集，確保正負樣本比例一致。全面導入 **五折分層交叉驗證 (Five-Fold Stratified Cross-Validation)**，有效防範模型過度擬合 (Overfitting)。
* **多模型建立與自動化調優**：建構五種主流分類演算法（LR, RF, XGBoost, SVM, KNN），並獨立運用 `RandomizedSearchCV` 進行超參數自動化優化，全面檢驗 Accuracy, Precision, Recall, F1-score, AUROC 與 AUPRC 指標。
* **可解釋性 AI (Explainable AI)**：透過特徵重要性分析 (Feature Importance) 透視黑箱模型，成功追溯出關鍵預測因子。

## 📊 實驗結果與效能評估

經過超參數精細調校後，各模型在五折分層交叉驗證中均展現優異效能，其中以邏輯迴歸與 XGBoost 表現最佳：

| 評估模型 (Models) | 交叉驗證 AUROC (CV AUROC) | 核心特徵重要性 (Key Features) |
| :--- | :---: | :--- |
| **Logistic Regression (LR)** | **0.922** | 學業壓力 (Academic Pressure)、自殺念頭 (Suicidal Thoughts) |
| **Extreme Gradient Boosting (XGBoost)** | **0.921** | 睡眠品質 (Sleep Quality)、工作/學習壓力 |
| Random Forest (RF) | 0.915 | 社交互動、生活型態變數 |

> **研究洞察**：本實驗成功驗證機器學習方法在心理健康風險評估上的可行性。模型不僅追求高預測準確率，更具備高度實務決策的可解釋性。

## 🛠️ 開發環境與使用套件
* **語言**: Python 3.x
* **核心套件**: 
  * 資料處理: `pandas`, `numpy`
  * 機器學習/特徵工程: `scikit-learn`
  * 梯度提升框架: `xgboost`
  * 數據視覺化: `matplotlib`, `seaborn`

## 📦 如何在本地端執行本專案

1. **複製本專案倉庫 (Clone Repository)**
```bash
   git clone [https://github.com/你的GitHub帳號/student-depression-prediction.git](https://github.com/你的GitHub帳號/student-depression-prediction.git)
   cd student-depression-prediction
