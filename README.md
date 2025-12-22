# 💳 Credit Card Fraud Detection using DBSCAN Clustering

[![Python](https://img.shields.io/badge/Python-3.7+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-orange.svg)](https://scikit-learn.org/)

An unsupervised machine learning approach to detect fraudulent credit card transactions using DBSCAN (Density-Based Spatial Clustering of Applications with Noise) clustering algorithm.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## 🎯 Overview

This project implements an **unsupervised anomaly detection system** for identifying potentially fraudulent credit card transactions. Unlike supervised approaches, DBSCAN doesn't require labeled training data and can identify outliers (potential fraud) based on transaction patterns and density.

### Why DBSCAN?

- **No labeled data required** - Works as an unsupervised approach
- **Identifies outliers** - Transactions marked as noise (-1) may indicate fraud
- **Handles varying density** - Can detect fraud patterns of different shapes
- **Robust to noise** - Doesn't force every point into a cluster

## ✨ Features

- 📊 **Automated Data Processing** - Handles missing values and infinite entries
- 🔄 **Feature Standardization** - Normalizes data for optimal clustering
- 🎯 **DBSCAN Clustering** - Density-based anomaly detection
- 📈 **PCA Visualization** - 2D projection of high-dimensional data
- 🧩 **Silhouette Score** - Quality metric for cluster separation
- 🎨 **Interactive Plots** - Visual representation of clusters and outliers

## 🚀 Installation

### Prerequisites

- Python 3.7 or higher
- Google Colab (recommended) or local Jupyter environment

### Dependencies

```bash
pip install pandas numpy matplotlib scikit-learn
```

### Clone Repository

```bash
git clone https://github.com/zain-cs/credit-card-fraud-dbscan.git
cd credit-card-fraud-dbscan
```

## 💻 Usage

### Running in Google Colab

1. Upload the notebook to Google Colab
2. Run all cells sequentially
3. Upload your credit card transaction CSV when prompted
4. View results and visualizations

### Running Locally

```python
# Import required libraries
import pandas as pd
import numpy as np
from sklearn.cluster import DBSCAN
from sklearn.preprocessing import StandardScaler

# Load your dataset
df = pd.read_csv('your_credit_card_data.csv')

# Follow the steps in the main script
# (See credit_card_fraud_dbscan.py)
```

### Code Structure

```
credit-card-fraud-dbscan/
│
├── credit_card_fraud_dbscan.py    # Main clustering script
├── README.md                       # This file
├── requirements.txt                # Python dependencies
├── LICENSE                         # MIT License
└── examples/
    └── sample_output.png           # Example visualization
```

## 📊 Dataset

This project works with credit card transaction datasets containing numerical features. The expected format:

- **Features**: V1, V2, ..., V28 (PCA-transformed features)
- **Time**: Seconds elapsed between transactions
- **Amount**: Transaction amount
- **Class** (optional): 0 = Normal, 1 = Fraud (for validation only)

### Recommended Dataset

[Kaggle Credit Card Fraud Detection Dataset](https://www.kaggle.com/mlg-ulb/creditcardfraud)

### Data Format

```csv
Time,V1,V2,V3,...,V28,Amount,Class
0,-1.359807134,-0.072781,...,149.62,0
1,-1.358354062,1.191857,...,2.69,0
```

## 🔬 Methodology

### 1. Data Preprocessing
- Remove infinite and missing values
- Select only numerical features
- Standardize features (mean=0, std=1)

### 2. DBSCAN Clustering
```python
DBSCAN(eps=1.5, min_samples=5)
```
- **eps**: Maximum distance between neighbors (tunable)
- **min_samples**: Minimum points to form a dense region

### 3. Anomaly Detection
- Points labeled as `-1` are **outliers** (potential fraud)
- Dense clusters represent normal transaction patterns
- Noise points deviate significantly from normal behavior

### 4. Evaluation
- **Silhouette Score**: Measures cluster cohesion (excluding noise)
- **Cluster Distribution**: Shows normal vs. outlier counts
- **PCA Visualization**: 2D representation of clusters

## 📈 Results

### Expected Output

```
📊 Cluster Distribution:
 0     280000
-1      1500
 1       500
```

- **Cluster 0**: Normal transactions (majority)
- **Cluster -1**: Outliers (potential fraud)
- **Other clusters**: Distinct transaction patterns

### Interpretation

🔴 **High Priority**: Transactions in cluster `-1` (noise/outliers)  
🟡 **Medium Priority**: Small, isolated clusters  
🟢 **Low Priority**: Large, dense clusters

### Sample Visualization

The PCA plot shows:
- **Dense regions** = Normal transaction clusters
- **Scattered points** = Outliers/potential fraud
- **Color coding** = Different cluster assignments

## ⚙️ Hyperparameter Tuning

Adjust DBSCAN parameters for your dataset:

```python
# More sensitive to outliers
DBSCAN(eps=0.5, min_samples=3)

# More conservative
DBSCAN(eps=2.0, min_samples=10)
```

**Guidelines:**
- **Smaller eps** → More outliers detected (higher sensitivity)
- **Larger min_samples** → Fewer small clusters (more conservative)

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📧 Contact

**Zain**  
GitHub: [@zain-cs](https://github.com/zain-cs)

## 🙏 Acknowledgments

- [Scikit-learn](https://scikit-learn.org/) for machine learning tools
- [Kaggle](https://www.kaggle.com/) for providing datasets
- Credit card fraud detection research community

## 📚 References

- Ester, M., et al. (1996). "A density-based algorithm for discovering clusters"
- Credit Card Fraud Detection Dataset (Kaggle)
- Scikit-learn DBSCAN Documentation

---

**⭐ If you found this project helpful, please consider giving it a star!**

---

### 🔄 Recent Updates

- **v1.0.0** (2024-12-22): Initial release with DBSCAN clustering implementation