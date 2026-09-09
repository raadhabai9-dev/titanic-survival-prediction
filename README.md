# titanic-survival-prediction
#  Titanic Survival Prediction  An interactive **Machine Learning web application** that predicts Titanic passenger survival using **Logistic Regression** and a **Decision Tree**. The entire ML pipeline runs directly in the browser with no backend or external API.  
#  Titanic Survival Prediction

An interactive **Machine Learning web application** that predicts Titanic passenger survival using **Logistic Regression** and a **Decision Tree**. The entire ML pipeline runs directly in the browser with no backend or external API.

The application provides dataset analysis, feature engineering, model training, performance evaluation, passenger-level predictions, visualizations, and downloadable PDF reports.

##  Features

*  Interactive Titanic dataset dashboard
*  Two machine learning models:

  * Logistic Regression using TensorFlow.js
  * Decision Tree implemented from scratch
*  Passenger survival prediction
*  Model performance comparison
*  Accuracy, Precision, Recall, F1 Score, and ROC-AUC
*  Confusion matrix visualization
*  Feature importance and model coefficient analysis
*  Passenger-level analysis
*  Interactive charts using Recharts
*  Automatic missing-value handling
*  Feature engineering
*  Downloadable PDF prediction reports
*  Fully client-side — no backend required
*  No external APIs required

##  Machine Learning Pipeline

The application follows a complete ML workflow:

```text
Titanic CSV Dataset
        ↓
Data Validation & Cleaning
        ↓
Missing Value Imputation
        ↓
Feature Engineering
        ↓
80/20 Train-Test Split
        ↓
Feature Normalization
        ↓
 ┌───────────────────────┐
 │                       │
 ▼                       ▼
Logistic Regression   Decision Tree
(TensorFlow.js)       (From Scratch)
 │                       │
 └───────────┬───────────┘
             ↓
      Model Evaluation
             ↓
      Survival Prediction
```

##  Data Preprocessing

The application validates the Titanic dataset and removes invalid or duplicate passenger records.

Missing values are handled using:

* **Age:** Median imputation
* **Fare:** Median imputation
* **Embarked:** Mode imputation

Categorical variables are converted into numerical features for machine learning.

### Engineered Features

The models use the following features:

* `Pclass`
* `Sex_encoded`
* `Age`
* `Fare`
* `SibSp`
* `Parch`
* `FamilySize`
* `IsAlone`
* `Embarked_C`
* `Embarked_Q`
* `Embarked_S`

Additional features such as **Family Size** and **Is Alone** are derived from the original passenger information.

##  Machine Learning Models

### Logistic Regression

Logistic Regression is implemented using **TensorFlow.js**.

The model uses:

* A single dense output unit
* Sigmoid activation
* Binary cross-entropy loss
* Adam optimizer
* 60 training epochs
* Min-max feature normalization

The model outputs a survival probability between 0 and 1.

### Decision Tree

A **CART-style Decision Tree** is implemented from scratch without relying on an external ML library.

It uses:

* Gini impurity
* Recursive binary splitting
* Configurable maximum depth
* Minimum samples per leaf
* Feature importance based on impurity reduction

The default maximum tree depth is **5**.

##  Model Evaluation

Both models are trained using the same deterministic **80/20 train-test split**, allowing a fair comparison.

The application calculates:

| Metric           | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| Accuracy         | Overall percentage of correct predictions                    |
| Precision        | Proportion of predicted survivors that actually survived     |
| Recall           | Proportion of actual survivors correctly identified          |
| F1 Score         | Harmonic mean of precision and recall                        |
| ROC-AUC          | Ability of the model to distinguish between survival classes |
| Confusion Matrix | TP, TN, FP and FN breakdown                                  |

Predictions use a default probability threshold of **0.5**.

##  Dashboard

The dashboard provides an overview of the Titanic dataset, including:

* Total passengers
* Survived passengers
* Non-survived passengers
* Overall survival rate
* Average passenger age
* Average fare
* Survival distribution
* Survival rate by gender
* Survival rate by passenger class
* Age distribution
* Fare distribution
* Dataset-derived insights

##  Survival Prediction

Users can enter a passenger profile including:

* Passenger class
* Sex
* Age
* Number of siblings/spouses
* Number of parents/children
* Fare
* Port of embarkation

The application automatically calculates:

* Family Size
* Whether the passenger is travelling alone

The selected ML model then produces a survival probability and classifies the passenger as:

**Likely Survived** or **Likely Not Survived**

> Predictions are model-based estimates derived from historical Titanic data and should not be interpreted as certainty.

##  PDF Reports

The application can generate a downloadable PDF report containing:

* Dataset summary
* Model performance metrics
* Confusion matrix
* Current prediction
* Model information
* Dataset insights
* Visualization/chart output

PDF generation is handled using **jsPDF** and **html2canvas**.

##  Tech Stack

### Frontend

* React 18
* Vite
* Tailwind CSS

### Machine Learning

* TensorFlow.js
* Custom JavaScript Decision Tree implementation

### Data Processing

* PapaParse
* Custom preprocessing and feature engineering

### Visualization

* Recharts

### Reporting

* jsPDF
* html2canvas

##  Project Structure

```text
titanic-survival-prediction/
│
├── public/
│   └── data/
│       └── titanic.csv
│
├── src/
│   ├── components/
│   │   ├── ChartCard.jsx
│   │   ├── ConfusionMatrix.jsx
│   │   ├── Header.jsx
│   │   ├── ModelMetrics.jsx
│   │   ├── PassengerDetails.jsx
│   │   ├── PassengerTable.jsx
│   │   ├── PredictionForm.jsx
│   │   ├── PredictionResult.jsx
│   │   ├── ReportButton.jsx
│   │   ├── Sidebar.jsx
│   │   └── StatCard.jsx
│   │
│   ├── ml/
│   │   ├── decisionTree.js
│   │   ├── logisticRegression.js
│   │   ├── modelTraining.js
│   │   └── preprocessing.js
│   │
│   ├── pages/
│   │   ├── Dashboard.jsx
│   │   ├── ModelPerformance.jsx
│   │   ├── PassengerAnalysis.jsx
│   │   └── PredictSurvival.jsx
│   │
│   ├── services/
│   │   └── dataset.js
│   │
│   ├── utils/
│   │   ├── featureEngineering.js
│   │   ├── insights.js
│   │   ├── metrics.js
│   │   └── reportGenerator.js
│   │
│   ├── App.jsx
│   ├── index.css
│   └── main.jsx
│
├── index.html
├── package.json
├── tailwind.config.js
├── vite.config.js
└── README.md
```

##  Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/your-username/titanic-survival-prediction.git
cd titanic-survival-prediction
```

### 2. Install dependencies

```bash
npm install
```

### 3. Start the development server

```bash
npm run dev
```

Open the local URL displayed by Vite in your browser.

### 4. Build for production

```bash
npm run build
```

##  Dataset

The project includes a Titanic passenger dataset at:

```text
public/data/titanic.csv
```

The application expects the following columns:

```text
PassengerId
Survived
Pclass
Name
Sex
Age
SibSp
Parch
Fare
Embarked
```

You can replace the dataset with another compatible CSV while maintaining these column names and expected values.

##  Architecture

This project is intentionally **frontend-only**.

There is:

* No Python backend
* No Flask/FastAPI server
* No database
* No external ML API
* No cloud inference service

Data processing, model training, evaluation, and prediction all happen inside the user's browser.

This makes the application easy to deploy as a static web application.

##  Learning Objectives

This project demonstrates how a complete machine learning workflow can be integrated into a modern frontend application.

Key concepts demonstrated include:

* Data cleaning
* Missing-value imputation
* Categorical encoding
* Feature engineering
* Train-test splitting
* Feature normalization
* Logistic Regression
* Decision Trees
* Gini impurity
* Model evaluation
* ROC-AUC calculation
* Confusion matrices
* Feature importance
* Client-side machine learning
* Interactive data visualization
* PDF report generation

##  Future Improvements

Potential improvements include:

* Add Random Forest and other ML algorithms
* Add hyperparameter tuning
* Add cross-validation
* Add ROC curves and precision-recall curves
* Add model training history visualization
* Allow users to upload custom datasets
* Add model persistence using IndexedDB
* Add more advanced passenger-level analytics
* Deploy the application using GitHub Pages or Vercel

## Disclaimer

This project is intended for **educational and demonstration purposes**.

The predictions are generated by machine learning models trained on historical Titanic passenger data. They represent statistical predictions rather than guaranteed outcomes.

##  Author

**Your Name**

If you found this project useful, consider giving the repository a ⭐ on GitHub.
