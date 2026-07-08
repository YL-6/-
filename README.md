# Water Quality Prediction

## English Version

### Project Overview

This project analyzes a water-quality dataset and builds machine learning models to predict whether a water sample is classified as safe or unsafe. The target variable is `Target`, where:

- `0` = Safe water
- `1` = Unsafe water

The project combines data cleaning, exploratory data analysis, domain knowledge, statistical interpretation, and supervised machine learning. The main goal is to identify important predictors associated with unsafe water and compare the predictive performance of different models.

The final merged notebook is:

`notebooks/Final_Project.ipynb`

### Dataset

The dataset comes from Kaggle:

`Water Quality Prediction`

Expected local data paths:

- Raw data: `data/raw/Water Quality Prediction.csv`
- Cleaned data: `data/processed/water_quality_cleaned.csv`

The dataset contains physicochemical and environmental water-quality indicators, including variables such as pH, iron, nitrate, chloride, lead, turbidity, fluoride, copper, sulfate, conductivity, chlorine, manganese, total dissolved solids, water temperature, air temperature, color, odor, and water source.

### Project Structure

```text
Project/
|-- data/
|   |-- raw/
|   |   `-- Water Quality Prediction.csv
|   `-- processed/
|       `-- water_quality_cleaned.csv
|-- domain_knowledge/
|   `-- water_quality_regulatory_background.md
|-- notebooks/
|   |-- 01_data_cleaning_V0616.ipynb
|   |-- 02_edaV0622.ipynb
|   |-- 03_model_1.ipynb
|   |-- 04_model_2.ipynb
|   |-- 05_model_3.ipynb
|   |-- 06_model_4.ipynb
|   |-- 07_model_5.ipynb
|   `-- Final_Project.ipynb
|-- reports/
|   |-- figures/
|   `-- model_results/
|-- FINAL_PROJECT_TASKS_SS26.pdf
`-- README.md
```

### Workflow

The final notebook follows the complete project workflow:

1. **Data Cleaning**

   The raw dataset is loaded, inspected, cleaned, and saved as a processed CSV file for later analysis.

2. **Exploratory Data Analysis**

   The cleaned dataset is explored through target distribution, numerical summaries, feature distributions, correlation analysis, categorical analysis, and outlier detection.

3. **Logistic Regression**

   Logistic Regression is used as an interpretable linear baseline model. Interaction features and hyperparameter tuning are included to improve performance and interpretability.

4. **Decision Tree**

   A Decision Tree model is trained as a non-linear single-tree baseline. The model is tuned using GridSearchCV and interpreted using feature importance and tree visualization.

5. **K-Nearest Neighbors**

   KNN is used as a distance-based classifier. Feature scaling, elbow search, hyperparameter search, and final test-set evaluation are included.

6. **Neural Network**

   A feedforward neural network is trained using class weights, early stopping, and stratified cross-validation. Permutation importance is used to improve interpretability.

7. **Ensemble Models**

   Random Forest and HistGradientBoosting are used to represent bagging and boosting approaches. The ensemble models are compared with the tuned Decision Tree baseline and interpreted using feature-importance methods.

### Models Used

The project compares the following supervised classification models:

- Logistic Regression
- Decision Tree
- K-Nearest Neighbors
- Neural Network
- Random Forest
- HistGradientBoosting

### Evaluation Metrics

The models are evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- PR-AUC for selected ensemble-model analysis

Because unsafe water is the more important class from a public-health perspective, recall and F1-score for the unsafe class are especially important.

### Outputs

Main output files are saved in:

- Figures: `reports/figures/`
- Model result tables: `reports/model_results/`

### How to Run

1. Open the project folder.
2. Make sure the raw dataset is located at:

   `data/raw/Water Quality Prediction.csv`

3. Install the required Python packages:

   ```bash
   pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn tqdm tensorflow jupyter
   ```

4. Open and run the final notebook:

   `notebooks/Final_Project.ipynb`

5. Run the notebook from top to bottom. The notebook assumes that relative paths are resolved from the `notebooks/` folder.

### Important Interpretation Note

This project predicts the dataset's `Target` variable. It does not certify that a water sample is legally potable under WHO, EU, or national drinking-water regulations. Some important drinking-water indicators, such as microbiological indicators and several regulated contaminants, are not included in the dataset. Therefore, the results should be interpreted as predictive evidence within this dataset rather than as a formal drinking-water safety assessment.

---

## 中文版本

### 项目简介

本项目基于水质数据集进行数据分析和机器学习建模，目标是预测水样本在数据集中被标记为安全还是不安全。目标变量为 `Target`，其含义为：

- `0` = 安全水样本
- `1` = 不安全水样本

本项目包括数据清洗、探索性数据分析、领域知识解释、统计分析和监督式机器学习建模。核心目标是识别与不安全水样本相关的重要预测变量，并比较不同模型的预测表现。

最终合并版 notebook 为：

`notebooks/Final_Project.ipynb`

### 数据集

本项目使用 Kaggle 上的 Water Quality Prediction 数据集。

本地数据路径如下：

- 原始数据：`data/raw/Water Quality Prediction.csv`
- 清洗后数据：`data/processed/water_quality_cleaned.csv`

数据集中包含多个水质相关的物理化学和环境指标，例如 pH、Iron、Nitrate、Chloride、Lead、Turbidity、Fluoride、Copper、Sulfate、Conductivity、Chlorine、Manganese、Total Dissolved Solids、Water Temperature、Air Temperature、Color、Odor 和 Source 等变量。

### 项目结构

```text
Project/
|-- data/
|   |-- raw/
|   |   `-- Water Quality Prediction.csv
|   `-- processed/
|       `-- water_quality_cleaned.csv
|-- domain_knowledge/
|   `-- water_quality_regulatory_background.md
|-- notebooks/
|   |-- 01_data_cleaning_V0616.ipynb
|   |-- 02_edaV0622.ipynb
|   |-- 03_model_1.ipynb
|   |-- 04_model_2.ipynb
|   |-- 05_model_3.ipynb
|   |-- 06_model_4.ipynb
|   |-- 07_model_5.ipynb
|   `-- Final_Project.ipynb
|-- reports/
|   |-- figures/
|   `-- model_results/
|-- FINAL_PROJECT_TASKS_SS26.pdf
`-- README.md
```

### 分析流程

最终 notebook 按照完整数据分析项目流程组织：

1. **数据清洗**

   读取原始数据，检查数据结构、缺失值和异常值，并输出清洗后的数据文件。

2. **探索性数据分析**

   分析目标变量分布、数值变量分布、变量相关性、类别变量模式以及异常值情况。

3. **Logistic Regression**

   使用逻辑回归作为可解释的线性基准模型，并加入交互项和超参数调优。

4. **Decision Tree**

   使用决策树作为非线性单树模型，并通过 GridSearchCV 进行调参，同时分析特征重要性和树结构。

5. **K-Nearest Neighbors**

   使用 KNN 作为基于距离的分类模型，包含特征缩放、K 值选择、超参数搜索和最终测试集评估。

6. **Neural Network**

   使用前馈神经网络进行二分类建模，并加入 class weights、early stopping、交叉验证和 permutation importance。

7. **Ensemble Models**

   使用 Random Forest 和 HistGradientBoosting 分别代表 bagging 和 boosting 方法，并与调参后的 Decision Tree baseline 进行比较。


### 使用的模型

本项目比较了以下监督式分类模型：

- Logistic Regression
- Decision Tree
- K-Nearest Neighbors
- Neural Network
- Random Forest
- HistGradientBoosting

### 评价指标

模型使用以下指标进行评估：

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- PR-AUC，主要用于 ensemble 模型分析

由于不安全水样本在公共健康场景中更重要，因此 unsafe 类的 recall 和 F1-score 是尤其重要的评价指标。

### 输出文件

主要输出文件保存在：

- 图像结果：`reports/figures/`
- 模型结果表：`reports/model_results/`


### 运行方式

1. 打开项目文件夹。
2. 确认原始数据文件位于：

   `data/raw/Water Quality Prediction.csv`

3. 安装所需 Python 包：

   ```bash
   pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn tqdm tensorflow jupyter
   ```

4. 打开并运行最终 notebook：

   `notebooks/Final_Project.ipynb`

5. 从上到下依次运行 notebook。该 notebook 使用相对路径，默认从 `notebooks/` 文件夹运行。

### 重要解释说明

本项目预测的是数据集中的 `Target` 变量，并不等同于依据 WHO、欧盟或国家饮用水法规对水样进行正式的可饮用水认证。数据集中缺少部分关键饮用水指标，例如微生物指标和若干受监管污染物。因此，本项目结果应被理解为该数据集内部的预测性证据，而不是正式的饮用水安全评估结论。
