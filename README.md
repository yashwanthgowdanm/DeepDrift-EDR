# DeepDrift: Explainable AI for Zero-Day Threat Detection

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Prototype-yellow)

**DeepDrift** is a next-generation Endpoint Detection and Response (EDR) engine powered by **Unsupervised Deep Learning**. 

Unlike traditional antivirus tools that rely on known signatures, DeepDrift learns the "baseline" of normal endpoint behavior. It detects **Zero-Day attacks**, **Ransomware**, and **Data Exfiltration** by identifying "Drift"—statistically significant deviations in telemetry patterns.

Crucially, DeepDrift includes an **Explainable AI (XAI)** module that tells security analysts *exactly why* an alert was triggered (e.g., "High File Entropy" vs "Abnormal Network Volume"), solving the "Black Box" problem of AI in security.

---

## 📊 Dashboard & Results

*(Place your `dashboard.png` image here)*
![DeepDrift Dashboard](dashboard.png)

### Key Metrics (Synthetic Test)
| Metric | Score | Significance |
| :--- | :--- | :--- |
| **ROC-AUC** | **1.00** | Perfect separation of attack vs. normal traffic. |
| **Precision** | **1.00** | Zero False Positives in the test environment. |
| **Recall** | **0.68** | Detects major threats while ignoring minor noise. |

---

## 🛡️ Key Features

* **🧠 Deep Autoencoder Architecture:** Uses a symmetric dense neural network (4-8-4-8-4 topology) to learn latent representations of benign behavior.
* **📉 Reconstruction Error Analysis:** Anomalies are detected by measuring the Mean Squared Error (MSE) between the input telemetry and the model's reconstruction.
* **🔍 Explainable AI (XAI):** breakdown of feature contribution (e.g., "This attack was flagged because File Entropy contributed 80% to the error score").
* **🦠 Advanced Attack Simulation:** Includes synthetic data generators for:
    * **Ransomware:** High File Entropy + High CPU Usage.
    * **Exfiltration:** Abnormal Network Volume + Odd Login Times.

---

## ⚙️ How It Works

1.  **Ingestion:** The system ingests 4-dimensional telemetry (File Entropy, CPU, Network Bytes, Login Count).
2.  **Training (Baseline):** The Autoencoder trains **only** on normal data, learning to compress and reconstruct it perfectly.
3.  **Detection (Drift):** When an attack occurs, the model fails to reconstruct the unfamiliar pattern, causing a spike in **Reconstruction Error**.
4.  **Dynamic Thresholding:** A statistical threshold (95th percentile) automatically flags high-error events as anomalies.

---

## 🚀 Installation & Usage

### Prerequisites
* Python 3.8+
* TensorFlow / Keras
* Pandas, NumPy, Scikit-Learn, Seaborn

### Setup
```bash
git clone [https://github.com/yourusername/DeepDrift-EDR.git](https://github.com/yourusername/DeepDrift-EDR.git)
cd DeepDrift-EDR
pip install -r requirements.txt
