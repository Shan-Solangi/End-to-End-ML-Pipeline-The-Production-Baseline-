📊 End-to-End Customer Churn ML Pipeline
A production-ready, end-to-end machine learning repository designed to predict customer churn. This project encapsulates the entire feature engineering, data preprocessing, and modeling workflow into a single, reusable Scikit-learn Pipeline API object, optimized via GridSearchCV to prevent data leakage during hyperparameter tuning.

🏗️ Pipeline Architecture & Outputs
The project separates source logic from generated evaluation assets to maintain a clean workspace footprint:

Plaintext
├── src/
│   └── train.py                     # Execution script for preprocessing, tuning, and evaluation
├── models/
│   └── best_pipeline.joblib          # Fully serialized production-ready artifact (Transformer + Model)
└── reports/
    ├── metrics.json                 # Optimal hyperparameters, Test Accuracy, and ROC-AUC scores
    └── classification_report.txt    # Per-class Precision, Recall, and F1-score breakdowns
🛠️ Developer Note: For complete, deep-dive architectural documentation detailing the code implementation and engineering decisions, please read the docs/DEVELOPER_GUIDE.md.

🚀 Quick Start
Follow these steps to set up your environment, execute the pipeline optimization, and export the production model.

1. Environment Setup
Clone this repository and isolate your dependencies inside a clean virtual environment:

Bash
# Clone the repository
git clone https://github.com/your-username/customer-churn-pipeline.git
cd customer-churn-pipeline

# Create and activate a virtual environment
python -bin venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate

# Install required packages
pip install -r requirements.txt
2. Run the Pipeline Execution
Execute the automated training script. This script handles data loading, scales numerical features, encodes categorical values, performs a grid search across multiple algorithms (e.g., Logistic Regression, Random Forest), and evaluates the champion model:

Bash
python src/train.py
🔑 Key Features Demonstrated
Data Leakage Prevention: Preprocessing transformers (scaling and encoding matrices) are bound directly within the Cross-Validation loop via Scikit-learn's Pipeline API.

Automated Optimization: Executes a GridSearchCV sweep across distinct hyperparameter combinations to locate the optimal trade-off between bias and variance.

Production Deployment Ready: The final exported .joblib file requires no external data manipulation steps. Passing a raw, unstructured dictionary or JSON payload directly into pipeline.predict() handles all data transformations seamlessly upstream.
