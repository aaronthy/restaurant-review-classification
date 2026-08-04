# 🍽️ Restaurant Review Intelligence Platform

An end-to-end NLP application that classifies restaurant reviews and turns unstructured customer feedback into actionable operational insights.

Built with Python, scikit-learn, FastAPI, and Streamlit, this project shows how natural language processing can support data-driven restaurant management by surfacing recurring customer issues and visualizing operational trends.

**[Repository](https://github.com/aaronthy/restaurant-review-intelligence-system)**

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-REST_API-009688?style=flat-square&logo=fastapi&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)

---

## Why I Built This

After five years managing a high-volume restaurant, I saw firsthand that customer reviews were a goldmine of operational insight — but reading through hundreds of them manually to spot patterns in food quality, wait times, cleanliness, or staffing is slow, subjective, and doesn't scale.

This project explores how machine learning can automate that process: categorizing feedback, surfacing recurring problems, and helping managers make faster, data-driven decisions.

Rather than building just a text classifier, the goal was a complete AI application spanning the full stack:

- 🤖 Machine learning model
- 🔌 REST API
- 📊 Interactive dashboard
- 📈 Business analytics
- 💡 Operational recommendations

---

## Features

### Machine Learning
- TF-IDF vectorization (unigrams + bigrams)
- LinearSVC classifier
- Handles class imbalance via controlled resampling and class weighting
- Model versioning with automatic timestamping
- Experiment tracking via `metrics.csv`

### Prediction Service
- FastAPI REST API for real-time review classification
- Top-3 category predictions with confidence scores

### Interactive Applications

**Streamlit Review Assistant**
- Chat-style interface for instant predictions
- Top-3 predicted categories, no coding required to test

**Restaurant Operations Dashboard**
- Category distribution and sentiment trends
- Average ratings and complaint frequency
- Operational KPIs and automated business recommendations

---

## Project Workflow

```text
Restaurant Reviews
        │
        ▼
Data Cleaning & Labeling
        │
        ▼
TF-IDF Vectorization
        │
        ▼
LinearSVC Classification Model
        │
 ┌──────┴──────────┐
 ▼                  ▼
FastAPI API     Streamlit Dashboard
        │
        ▼
Business Insights & Operational Recommendations
```

---

## Machine Learning Model

| Component       | Method                                        |
|------------------|------------------------------------------------|
| Vectorizer       | TF-IDF (unigrams + bigrams)                    |
| Classifier       | LinearSVC                                       |
| Class Handling   | Controlled resampling + `class_weight="balanced"` |

**Example**

Input:
```text
"The food was cold and the service was extremely slow."
```

Prediction: `food_quality`

Top-3 predictions:
```json
{
  "top_3": ["food_quality", "waiting_time", "service"]
}
```

---

## Model Performance

| Metric    | Score |
|-----------|------:|
| Accuracy  | ~75%  |
| Macro F1  | ~0.68 |

Performance varies across categories due to class imbalance and overlapping operational labels such as **service** and **waiting_time**.

---

## Repository Structure

```text
restaurant-review-intelligence-system/
├── data/
│   ├── yelp_sample.csv
│   └── yelp_labeled.csv
│
├── models/
│   ├── text_classifier.joblib
│   ├── metrics.csv
│   └── vectorizer.joblib
│
├── src/
│   ├── analysis/
│   ├── app/
│   ├── api.py
│   ├── train_model.py
│   ├── predict.py
│   ├── chat_app.py
│   ├── label_data.py
│   └── load_yelp.py
│
├── images/
├── requirements.txt
└── README.md
```

---

## Dashboard Preview

### Restaurant Review Assistant

![Restaurant Review Assistant](images/chatapp1.png)
![Restaurant Review Assistant](images/chatapp2.png)

The Streamlit app lets users enter a customer review and get real-time category predictions with confidence scores.

### Restaurant Operations Dashboard

![Restaurant Operations Dashboard](images/dashboard1.png)
![Restaurant Operations Dashboard](images/dashboard2.png)
![Restaurant Operations Dashboard](images/dashboard3.png)

The dashboard visualizes operational trends and helps managers quickly spot recurring issues through interactive charts and KPI summaries, including:

- Review category distribution
- Lowest-rated operational category
- Most common customer complaints
- Automated business recommendations

---

## Business Insights

Analysis of **1,481 categorized customer reviews** revealed several operational trends:

- Food quality (34.7%) and price/value (30.8%) together account for over 65% of customer feedback.
- Wait time, staffing, and order accuracy appear less frequently, but are strongly associated with negative customer experiences.
- Operational issues often have an outsized impact on satisfaction relative to how often they're mentioned.

---

## Potential Business Value

This platform demonstrates how AI can help restaurant operators:

- Reduce manual review analysis time
- Detect recurring operational issues early
- Improve staffing decisions
- Monitor customer satisfaction trends
- Identify service bottlenecks
- Support data-driven operational improvements

---

## Challenges

- Class imbalance across categories
- Overlapping operational labels (e.g., service vs. waiting_time)
- Inconsistent manual labeling
- Limited labeled training data

These challenges reinforced the importance of data quality alongside model selection.

---

## Future Roadmap

- [ ] Replace TF-IDF with Sentence-BERT embeddings
- [ ] Support multi-label classification
- [ ] Containerize with Docker
- [ ] Deploy to the cloud (AWS/Azure)
- [ ] Migrate to a PostgreSQL backend
- [ ] Add a CI/CD pipeline
- [ ] LLM-generated management summaries
- [ ] Authentication and multi-user support

---

## Tech Stack

`Python` · `scikit-learn` · `pandas` · `NumPy` · `FastAPI` · `Streamlit` · `Joblib`

---

## Installation

```bash
git clone https://github.com/aaronthy/restaurant-review-intelligence-system.git
cd restaurant-review-intelligence-system
```

```bash
python -m venv venv
venv\Scripts\activate
```

```bash
pip install -r requirements.txt
```

**Train the model**
```bash
python src/train_model.py
```

**Run the API**
```bash
uvicorn src.api:app --reload
```

**Run the Streamlit assistant**
```bash
streamlit run src/chat_app.py
```

**Run the dashboard**
```bash
streamlit run src/app/dashboard.py
```

---

## About This Project

Developed independently as part of my transition into AI/ML engineering, this project combines hands-on restaurant operations experience with machine learning to show how AI can solve practical business problems through data-driven automation and analytics.

---

## Author

**Aaron Tsen Heng Yee**

[GitHub](https://github.com/aaronthy) · [LinkedIn](https://www.linkedin.com/in/aaron-tsen-heng-yee/)
