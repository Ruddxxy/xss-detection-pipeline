# XSS Detection Pipeline: A Hybrid Machine Learning Pipeline for XSS Detection

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.x-orange)
![Pandas](https://img.shields.io/badge/Pandas-2.x-yellow)
![License](https://img.shields.io/badge/License-MIT-green)

XSS Detection Pipeline is a sophisticated security tool that leverages a hybrid machine learning approach to detect Cross-Site Scripting (XSS) vulnerabilities in code snippets. It is designed not only to identify known XSS patterns but also to uncover novel and obfuscated threats through advanced feature engineering and anomaly detection.

## 🚀 Key Features

- **Hybrid Detection Model:** Combines an unsupervised **Isolation Forest** to flag anomalous (and potentially novel) threats with a supervised **Random Forest Classifier** trained on known XSS patterns for multi-layered defense.
- **Advanced Feature Engineering:** Goes beyond simple keyword matching by implementing:
    - **Deep Abstract Syntax Tree (AST) Traversal:** Parses JavaScript code to understand its structural and syntactic properties.
    - **Obfuscation Metrics:** Calculates **Shannon entropy** and token length to identify obfuscated or packed code, a common technique in advanced attacks.
    - **Extensive Regex Library:** Utilizes a library of over 30+ regex patterns to detect a wide range of XSS vectors, including those in SVGs, HTML tags, and encoded characters.
- **Rigorous Validation:** The model's performance is validated using **5-Fold Cross-Validation** to ensure stability and generalizability, consistently achieving a **Precision, Recall, and F1-Score of 0.97**.
- **In-depth Analysis:** Includes feature importance ranking, a **feature ablation study** to verify the impact of key predictors, and false negative analysis for continuous improvement.

## 🛠️ How It Works

The detection pipeline follows a systematic process to analyze and classify each code snippet:

1.  **Feature Extraction:** Each input string is passed through the `extract_ast_features` function, which generates a rich set of features based on its content and structure (AST properties, entropy, regex matches, etc.).
2.  **Vectorization:** The extracted feature strings are converted into a numerical format using a pre-fitted `TfidfVectorizer`.
3.  **Hybrid Prediction:**
    - The vectorized input is first evaluated by the **Isolation Forest**. If it's flagged as an anomaly, it's considered a potential threat.
    - It is then evaluated by the **Random Forest Classifier**, which predicts based on patterns learned from labeled data.
    - A snippet is classified as malicious if **either** model flags it as a threat, ensuring high sensitivity.

## ⚙️ Setup and Usage

To get started with XSS Detection Pipeline, follow these steps.

### Prerequisites

- Python 3.9+
- Pip (Python package installer)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/xss-detection-pipeline.git]
    cd xss-detection-pipeline
    ```

2.  **Install the required packages:**
    ```bash
    pip install pandas scikit-learn esprima
    ```

### Running the Detector

1.  **Prepare your data:** Ensure you have a `xss_processed.csv` file with a 'Sentence' column containing the code snippets and a 'Label' column (1 for malicious, 0 for benign).

2.  **Execute the script:** Run the Python script to preprocess the data, train the models, and run evaluations.
    ```python
    python your_script_name.py
    ```

3.  **Test new samples:** You can add new code snippets to the `test_samples` list in the script to see the model's predictions in real-time.

## 📊 Evaluation & Performance

The model was rigorously tested using 5-Fold Cross-Validation, yielding the following consistent results:

| Metric | Score |
| :--- | :--- |
| **Precision** | `0.97 ± 0.00` |
| **Recall** | `0.97 ± 0.00` |
| **F1-Score** | `0.97 ± 0.00` |

The project also includes a **feature ablation study** to confirm the high impact of features like `event_handlers` and `pattern_matches`, and **false negative analysis** to identify areas for future improvement.

## 📜 License

This project is licensed under the MIT License. See the `LICENSE` file for details.
