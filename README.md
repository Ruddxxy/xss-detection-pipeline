# XSS Attack Detection using Machine Learning

This project implements a **hybrid ML pipeline** to detect **Cross-Site Scripting (XSS)** attacks.  
The approach combines **AST-based structural features** and **TF-IDF lexical features** with a hybrid model:
- **Isolation Forest** → anomaly detection (flags unknown/novel payloads)
- **Random Forest** → supervised classification (predicts malicious vs benign)

---

## 🚀 Features
- Extracts **AST-based features** using `esprima` (function calls, DOM access, event handlers).
- Computes **entropy & token statistics** to detect obfuscation.
- Uses **TF-IDF vectorization** for lexical analysis.
- Hybrid ML pipeline catches both **known and obfuscated payloads**.
- Evaluation includes:
  - Classification report (precision, recall, F1)
  - Confusion matrix heatmap
  - Top feature importance chart

---

## 📊 Results
- **Precision:** ~98%  
- **Recall (malicious class):** ~98%  
- **F1-score:** ~98%  
- Robust against several obfuscation tricks.
- Reduced **false positives by 35%** compared to baseline models.  

Visualization examples included in the notebook:
- Confusion Matrix  
- Top-10 Feature Importances  

---

## 📂 Repository Contents
- `XSS_Detection.ipynb` → Full notebook with code, training, and evaluation  
- `requirements.txt` → Dependencies for reproducibility  
- Full dataset: [Kaggle XSS dataset](https://www.kaggle.com/datasets/syedsaqlainhussain/cross-site-scripting-xss-dataset-for-deep-learning)  

---

## ⚙️ Installation & Usage
Clone the repository and install dependencies:

```bash
git clone https://github.com/<your-username>/xss-detection-ml.git
cd xss-detection-ml
pip install -r requirements.txt
