# 👕 AI-Based Smart Clothing Size Recommendation System

An **AI/ML-based clothing size recommendation system** designed for an online fashion platform such as **Myntra**.

The project uses customer and product-related information to predict the most suitable clothing size from **XS, S, M, L, XL, and XXL**. The objective is to demonstrate how Machine Learning can be used to improve the online fashion shopping experience and potentially reduce size-related returns.

> **Note:** This is an academic demonstration project. The dataset is completely synthetic and does not contain real Myntra customer data.

---

## 🎯 Project Objective

Online clothing shopping can be difficult because customers cannot physically try the product before purchasing. Differences in sizing between brands and clothing categories can result in incorrect size selection.

This project aims to build a Machine Learning system that:

* Recommends a suitable clothing size
* Uses customer characteristics and purchase history
* Provides a prediction confidence score
* Demonstrates an interactive size recommendation system
* Shows how AI can support personalization in fashion e-commerce

---

## 💡 Business Problem

Incorrect clothing sizes can lead to:

* 📦 Higher product return rates
* 💰 Increased reverse-logistics costs
* 😕 Customer dissatisfaction
* 🛒 Cart abandonment
* 🌱 Additional environmental impact from unnecessary transportation

A personalized size recommendation system can help customers make more informed purchasing decisions.

---

## 🧠 Machine Learning Approach

This project uses **Supervised Machine Learning**, specifically a **classification problem**.

### Model Used

**Random Forest Classifier**

The model predicts one of six clothing-size classes:

`XS | S | M | L | XL | XXL`

The Random Forest model is trained using 2,000 records and evaluated using 500 unseen test records.

### Model Configuration

```text
Algorithm: Random Forest Classifier
Number of Trees: 100
Random State: 42
Class Weight: Balanced
```

---

## 📊 Dataset

The project creates a **synthetic dataset containing 2,500 records and 12 columns**.

### Features

| Feature            | Description                        |
| ------------------ | ---------------------------------- |
| Customer_ID        | Unique customer identifier         |
| Age                | Customer age                       |
| Gender             | Male/Female                        |
| Height_cm          | Customer height                    |
| Weight_kg          | Customer weight                    |
| Previous_Size      | Previously purchased clothing size |
| Brand              | Clothing brand                     |
| Category           | Clothing category                  |
| Fit_Preference     | Slim, Regular or Relaxed           |
| Previous_Purchases | Number of previous purchases       |
| Previous_Returns   | Number of previous returns         |
| Recommended_Size   | Target variable                    |

The target variable is `Recommended_Size`.

---

## 🔄 Project Workflow

```text
Synthetic Data Generation
          ↓
Exploratory Data Analysis
          ↓
Data Cleaning & Validation
          ↓
Feature Encoding & Preprocessing
          ↓
Train-Test Split
          ↓
Random Forest Model
          ↓
Model Evaluation
          ↓
Feature Importance Analysis
          ↓
Size Prediction
          ↓
Interactive Recommendation Demo
```

---

## 🔍 Exploratory Data Analysis

The dataset was checked for:

* Number of rows and columns
* Data types
* Missing values
* Duplicate records
* Descriptive statistics
* Recommended-size distribution
* Feature relationships

The generated dataset contains **2,500 records with no missing values and no duplicate rows** in the executed notebook.

---

## ⚙️ Data Preprocessing

The project prepares numerical and categorical features before training.

The dataset is divided into:

* **80% Training Data:** 2,000 records
* **20% Testing Data:** 500 records

After preprocessing:

* Training features: `2,000 × 23`
* Testing features: `500 × 23`

The preprocessing is fitted on the training data and then applied to the test data to help avoid data leakage.

---

## 🌲 Model Training

A Random Forest Classifier with **100 decision trees** is used.

```python
RandomForestClassifier(
    n_estimators=100,
    random_state=42,
    class_weight='balanced'
)
```

The model achieved the following results in the executed notebook:

| Metric            |  Result |
| ----------------- | ------: |
| Training Accuracy | 100.00% |
| Testing Accuracy  |  62.40% |

The difference between training and testing accuracy indicates that the model fits the synthetic training data very strongly but has more limited generalization performance on the test data.

---

## 📈 Model Evaluation

The project evaluates the classifier using:

* Accuracy
* Precision
* Recall
* F1-score
* Classification Report
* Confusion Matrix

The test accuracy is **62.40%**. The weighted average F1-score reported by the notebook is approximately **0.61**.

### Classification Performance

| Size | Precision | Recall | F1-Score |
| ---- | --------: | -----: | -------: |
| XS   |      0.00 |   0.00 |     0.00 |
| S    |      0.59 |   0.26 |     0.36 |
| M    |      0.65 |   0.77 |     0.70 |
| L    |      0.54 |   0.60 |     0.57 |
| XL   |      0.70 |   0.68 |     0.69 |
| XXL  |      0.67 |   0.20 |     0.31 |

These results should be interpreted in the context of the project's synthetic dataset rather than as evidence of real-world Myntra performance.

---

## 👤 Size Prediction

The notebook includes a reusable prediction function:

```python
predict_size(
    age,
    gender,
    height_cm,
    weight_kg,
    previous_size,
    brand,
    category,
    fit_preference,
    previous_purchases,
    previous_returns
)
```

The function returns:

1. **Predicted clothing size**
2. **Prediction confidence**

For example, one tested customer profile received a prediction of **M with 76% confidence**.

---

## 🖥️ Interactive Demo

The notebook also includes an interactive `ipywidgets` demonstration.

Users can adjust:

* Age
* Gender
* Height
* Weight
* Previous Size
* Brand
* Clothing Category
* Fit Preference
* Previous Purchases
* Previous Returns

The system then displays the recommended clothing size and prediction confidence.

---

## 💼 Business Value

If developed further with real-world data, a system like this could potentially help an online fashion platform with:

### 1. Reduced Size-Related Returns

Better size recommendations may reduce purchases made with incorrect sizing.

### 2. Better Customer Experience

Customers receive a personalized recommendation instead of relying only on generic size charts.

### 3. Improved Conversion

Reducing uncertainty around sizing may encourage customers to complete purchases.

### 4. Inventory Planning

Size-related patterns can provide useful information for inventory and product planning.

### 5. Personalization

The system can provide individualized recommendations based on customer and product characteristics.

---

## ⚠️ Limitations

This project has several important limitations:

* The dataset is **synthetic**, not real customer data.
* Only 2,500 records are used.
* Real clothing sizes can vary significantly between brands.
* The model uses a limited set of customer and product features.
* The prediction is limited to XS–XXL.
* Real-world sizing systems can change over time.
* There is currently no continuous customer-feedback loop.
* The model would require additional validation before real-world deployment.

---

## 🚀 Future Scope

The project can be improved by:

* Using larger real-world datasets
* Adding detailed body measurements
* Including garment measurements
* Adding fabric/stretch information
* Using customer reviews and fit feedback
* Adding recent purchase history
* Developing a web/mobile interface
* Comparing Random Forest with other ML algorithms
* Implementing continuous model retraining
* Deploying the model through an API
* Integrating the recommendation system into an e-commerce product page

---

## 🛠️ Technologies Used

* **Python**
* **Google Colab / Jupyter Notebook**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **IPyWidgets**

The notebook imports these data analysis, visualization, preprocessing and machine-learning libraries.

---

## 📁 Repository Structure

```text
Myntra-AI-ML-Size-Recommendation/
│
├── Myntra_AI_and_ML_model.ipynb
├── README.md
└── requirements.txt        # Optional
```

---

## ▶️ How to Run

### Option 1: Google Colab

1. Download or clone this repository.
2. Open `Myntra_AI_and_ML_model.ipynb`.
3. Upload it to Google Colab.
4. Run the notebook cells sequentially.
5. Follow the outputs and interactive recommendation demo.

### Option 2: Jupyter Notebook

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn ipywidgets
```

Then open:

```text
Myntra_AI_and_ML_model.ipynb
```

and run the cells sequentially.

---

## 📌 Academic Disclaimer

This project is created for **academic and demonstration purposes**.

The project uses a synthetic dataset generated within the notebook and does **not** use actual private customer information from Myntra. The model's accuracy should not be interpreted as actual performance of Myntra's systems.

---

## 👨‍💻 Project Summary

**Project:** AI-Based Smart Clothing Size Recommendation System
**Industry:** Fashion E-commerce
**Business Context:** Myntra
**ML Type:** Supervised Learning
**Problem Type:** Multi-Class Classification
**Algorithm:** Random Forest Classifier
**Dataset:** Synthetic
**Records:** 2,500
**Target:** Clothing Size (XS–XXL)
**Test Accuracy:** 62.40%

---

## ⭐ Key Takeaway

This project demonstrates how **Artificial Intelligence and Machine Learning can be applied to the fashion e-commerce industry** to create personalized clothing-size recommendations.

Although the current version is an academic prototype based on synthetic data, it provides a foundation for a more advanced real-world recommendation system that could combine customer measurements, purchase history, product characteristics and continuous feedback.
