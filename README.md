# Human Value Detection

This project presents a **deep learning-based approach** for detecting human values expressed in textual arguments using **BERT**. It explores the intersection of **machine learning**, **natural language processing (NLP)**, and **ethics**, with the goal of automatically identifying moral and ethical values (e.g., fairness, care, authority, loyalty) in text.

---

## 📌 Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Preprocessing](#preprocessing)
- [Model Architecture](#model-architecture)
- [Training](#training)
- [Evaluation & Results](#evaluation--results)
- [Applications](#applications)
- [Future Work](#future-work)
- [Installation & Usage](#installation--usage)
- [References](#references)

---

## 📝 Introduction
Artificial intelligence is increasingly shaping human interaction with technology. However, one challenge is enabling AI to understand **human values** behind language.  

This project leverages **BERT** in a **multi-label classification setup** to detect **21 distinct human values** in short text arguments. The aim is to support **ethical AI systems**, improve **content moderation**, and provide insights into **public discourse analysis**.

---

## 📊 Dataset
We used the **Touché23-ValueEval dataset**, consisting of:
- `argumentstest.tsv` → Short arguments (premise, conclusion, stance).
- `labelstest.tsv` → Binary labels for 21 values (e.g., Care, Fairness, Loyalty, Authority).

The datasets were merged using `Argument ID` to form a single structured dataset.

---

## 🔄 Preprocessing
Steps performed:
1. Merge arguments and labels into a unified dataset.
2. Combine premise, conclusion, and stance into a single text field.
3. Handle missing values by removing incomplete rows.
4. Visualize label distribution across all 21 values.
5. Split data into training (80%) and testing (20%).

---

## 🧠 Model Architecture
The classifier is built on **BERT** from Hugging Face’s Transformers library:
- **BERT Encoder** → Extracts contextual embeddings.
- **Dropout Layer** → Prevents overfitting.
- **Fully Connected Output Layer** → 21 sigmoid-activated nodes (multi-label classification).

Loss Function: `BCEWithLogitsLoss`  
Optimizer: `AdamW`  
Batch Size: 16–32  
Learning Rate: 2e-5  
Epochs: 3–5  

---

## ⚙️ Training
The model is fine-tuned on the dataset using the above hyperparameters. Training loss converged steadily within 3–5 epochs.

---

## 📈 Evaluation & Results
Evaluation metrics:
- **Accuracy**
- **Precision**
- **Recall**
- **F1-score**

### Sample Results (per-value):
| Value     | Precision | Recall | F1-score |
|-----------|-----------|--------|----------|
| Care      | 0.81      | 0.75   | 0.78     |
| Fairness  | 0.76      | 0.78   | 0.77     |
| Loyalty   | 0.65      | 0.62   | 0.63     |
| Authority | 0.72      | 0.70   | 0.71     |
| Sanctity  | 0.60      | 0.55   | 0.57     |

**Micro F1:** 0.73  
**Macro F1:** 0.66  

Key Observations:
- Frequent values (Care, Fairness) performed better.
- Rare values (Sanctity, Tradition) suffered due to class imbalance.

---

## 🚀 Applications
- **Content Moderation** → Better detection of ethical alignment in social media posts.  
- **Political Discourse Analysis** → Identifying value appeals in debates and speeches.  
- **Ethical AI Development** → Aligning AI decision-making with human values.  
- **Social Science Research** → Understanding cultural and temporal shifts in value expression.  
- **Recommendation Systems** → Recommending content aligned with user values.  

---

## 🔮 Future Work
- Expand dataset with diverse sources (e.g., Reddit, news articles).  
- Add **multilingual support**.  
- Implement **explainable AI** features.  
- Explore advanced transformer models (RoBERTa, DeBERTa, DistilBERT).  
- Deploy in **real-time applications** (moderation tools, chatbots, recommender systems).  

---

## ⚡ Installation & Usage
### 1. Clone the repository
```bash
git clone https://github.com/your-username/Human-Value-Detection.git
cd Human-Value-Detection
