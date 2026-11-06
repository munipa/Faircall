# ⚾ FAIRCALL
### Auditing the Strike Zone with Machine Learning

**FAIRCALL** is an applied machine learning project designed to evaluate MLB home-plate umpire performance by analyzing ball-strike decisions using historical pitch-level data.

The project uses machine learning to establish a baseline for pitch classification, evaluate umpire calling accuracy, and develop an interactive analytics platform for exploring umpire performance across multiple MLB seasons.

---

## 🎯 Project Objectives

The primary objectives of FAIRCALL are:

1. **Historical Data Collection:** Collect and process MLB Statcast pitch-level data from the 2023–2026 seasons.
2. **Baseline Machine Learning Model:** Develop a classification model to predict whether a pitch should be classified as a ball or called strike.
3. **Umpire Accuracy Analysis:** Compare actual umpire decisions against an independent strike-zone reference to evaluate individual umpire performance.
4. **Interactive Application:** Develop a web-based dashboard that allows users to explore model performance, pitch-level data, and umpire accuracy rankings.

## 🛠️ Technology Stack

| Component | Technologies |
|---|---|
| Programming Language | Python |
| Data Collection | pybaseball, MLB Stats API |
| Data Processing | Pandas, NumPy |
| Data Storage | Parquet, PyArrow |
| Machine Learning | Scikit-learn, XGBoost |
| Model Evaluation | Scikit-learn, SciPy |
| Data Visualization | Matplotlib, Seaborn, Plotly |
| Backend | FastAPI |
| Frontend | React, TypeScript, Tailwind CSS |
| Database | PostgreSQL / Supabase |
| Version Control | Git, GitHub |

## 🏗️ Project Architecture

FAIRCALL follows a modular Python architecture in which individual components are developed independently and coordinated through a central execution file.

### Overall Workflow

1. **Data Collection**
   - Retrieve Statcast pitch-level data.
   - Collect MLB umpire assignments.
   - Integrate relevant game and pitch information.

2. **Data Preprocessing**
   - Handle missing and invalid values.
   - Remove duplicate records.
   - Standardize dataset formats.
   - Associate pitches with the appropriate home-plate umpire.

3. **Feature Engineering**
   - Extract pitch location and characteristics.
   - Incorporate batter strike-zone dimensions.
   - Include count and game-context information.
   - Prepare training and testing datasets.

4. **Machine Learning**
   - Develop a Logistic Regression baseline model.
   - Implement XGBoost for model comparison.
   - Generate ball-strike classifications and probabilities.
   - Evaluate model performance.

5. **Umpire Performance Analysis**
   - Compare actual umpire calls against an independent strike-zone reference.
   - Calculate individual umpire performance metrics.
   - Generate an initial umpire accuracy leaderboard.

6. **Application Development**
   - Integrate analytical results into a backend API.
   - Develop an interactive frontend.
   - Display model performance and umpire rankings.

## 📁 Repository Structure

```text
FAIRCALL/
│
├── main.py
│
├── config/
│   └── settings.py
│
├── data/
│   ├── raw/
│   └── processed/
│
├── src/
│   ├── data_collection/
│   │   ├── __init__.py
│   │   ├── statcast.py
│   │   └── umpire_data.py
│   │
│   ├── preprocessing/
│   │   ├── __init__.py
│   │   ├── clean_data.py
│   │   └── feature_engineering.py
│   │
│   ├── modeling/
│   │   ├── __init__.py
│   │   ├── train_model.py
│   │   ├── evaluate_model.py
│   │   └── predict.py
│   │
│   ├── analytics/
│   │   ├── __init__.py
│   │   └── umpire_leaderboard.py
│   │
│   └── visualization/
│       ├── __init__.py
│       └── charts.py
│
├── models/
│
├── notebooks/
│   └── exploratory_analysis.ipynb
│
├── results/
│
├── requirements.txt
│
└── README.md
```

## 🤖 Machine Learning Approach

The initial FAIRCALL implementation focuses on binary classification of pitches.

**Target variable:**
- Ball
- Called Strike

**Potential input features:**
- Pitch location (`plate_x`, `plate_z`)
- Batter strike-zone dimensions
- Pitch velocity
- Pitch movement
- Pitch type
- Balls and strikes count

### Models

The initial implementation will evaluate two classification algorithms:

| Model | Purpose |
|---|---|
| Logistic Regression | Baseline classification model |
| XGBoost | Advanced model comparison |

### Evaluation Metrics

Model performance will be evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

The dataset will be split using a chronological or season-based approach to evaluate generalization to unseen games.

**Important:** Model classification performance and umpire accuracy are treated as separate measurements. Umpire accuracy requires an independent reference for whether each pitch was inside or outside the applicable strike zone.

## 📊 Umpire Accuracy Leaderboard

FAIRCALL will generate an initial leaderboard based on individual umpire performance.

The leaderboard will include:

| Metric | Description |
|---|---|
| Umpire Name | Identifies the home-plate umpire |
| Pitches Evaluated | Number of eligible pitches analyzed |
| Correct Calls | Number of calls matching the reference |
| Incorrect Calls | Number of calls differing from the reference |
| Accuracy | Percentage of correct calls |
| Sample Size | Number of evaluated observations |

Minimum sample-size requirements will be used to avoid misleading comparisons between umpires with substantially different numbers of evaluated pitches.

## 🖥️ Application Features

The planned FAIRCALL web application will provide the following functionality:

**1. Dashboard**
- Overview of analyzed pitches.
- Number of umpires evaluated.
- Baseline model performance.
- Season-level statistics.

**2. Umpire Leaderboard**
- Ranked umpire performance.
- Accuracy comparisons.
- Search and filtering capabilities.
- Pitch sample sizes.

**3. Model Performance**
- Accuracy, precision, recall and F1-score.
- Confusion matrix.
- Model comparisons.

**4. Pitch Explorer**
- Individual pitch information.
- Pitch location visualization.
- Actual umpire decision.
- Model classification and probability.

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

- Python 3.10+
- Git
- pip
- A code editor (VS Code recommended)

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>

cd FAIRCALL
```

### 2. Create a Virtual Environment

**Mac / Linux:**

```bash
python3 -m venv venv

source venv/bin/activate
```

**Windows:**

```bash
python -m venv venv

venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Execute the Pipeline

```bash
python main.py
```

The main execution file coordinates the individual modules and runs the FAIRCALL pipeline.

## 👥 Team & Contributions

FAIRCALL is developed collaboratively as an Applied Machine Learning project.

| Team Member | Primary Responsibility |
|---|---|
| Hugh | Data Collection and Preprocessing |
| Akhil | Machine Learning and Umpire Analytics |
| Soham | Application Development and Integration |

All team members contribute to testing, integration, documentation, and overall project development.

## 📅 Development Roadmap

### Midterm Milestones

- [ ] Collect Statcast data for the 2023–2026 seasons.
- [ ] Build and validate the data preprocessing pipeline.
- [ ] Develop the initial Logistic Regression baseline model.
- [ ] Evaluate model accuracy, precision, recall, and F1-score.
- [ ] Generate the first umpire accuracy leaderboard.
- [ ] Develop a clickable FAIRCALL application prototype.

### Future Development

- [ ] Compare additional machine learning algorithms.
- [ ] Expand contextual umpire performance analysis.
- [ ] Incorporate ABS challenge outcome data.
- [ ] Develop advanced umpire consistency metrics.
- [ ] Introduce automated performance reports.
- [ ] Expand application functionality and deployment.

## ⚖️ Project Scope & Limitations

FAIRCALL is an academic machine learning project intended to explore data-driven evaluation of MLB umpire performance.

Model predictions are statistical estimates and should not automatically be treated as definitive ground truth. Umpire evaluations must account for strike-zone definitions, sample sizes, data quality, and uncertainty.

The initial implementation focuses on called ball-strike decisions and does not attempt to evaluate every aspect of umpiring performance.

## 📄 License

This project is developed for academic and educational purposes. A formal open-source license will be added when the project licensing terms are finalized.

---

**FAIRCALL — Bringing Data-Driven Accountability to America's Pastime.** ⚾
