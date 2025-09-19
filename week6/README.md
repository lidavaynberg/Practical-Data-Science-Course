# Week 6: Intro to Predictive Analytics (without heavy math)

## 📚 Overview

Move from describing data to predicting outcomes! This week introduces machine learning concepts in an accessible way, focusing on interpretation and practical application rather than complex mathematics. Learn to build simple predictive models and explain what they mean in plain language.

## 🎯 Learning Objectives

By the end of this week, you will be able to:

- Understand the difference between describing and predicting data
- Split data into training and testing sets to validate predictions
- Build simple predictive models using decision trees and linear models
- Interpret model results and explain what predictions mean
- Evaluate how well a model performs using basic metrics
- Apply predictive models to social impact scenarios

## 🎓 Session Structure (80 minutes)

### Lecture (40 minutes): From Describing to Predicting

**Topics Covered:**
- What is machine learning and why it matters for social impact
- Supervised learning: learning from examples to make predictions
- Train/test split: why we need to test our models on new data
- Types of predictions:
  - **Classification**: Predicting categories (will a student graduate?)
  - **Regression**: Predicting numbers (what will income be?)
- Model types (focus on interpretation, not math):
  - **Decision trees**: Easy to understand rules
  - **Linear models**: Simple relationships between variables
- How to interpret and trust model results

### Tutorial (40 minutes): Building Your First Predictive Model

**Hands-on Activities:**
- Use scikit-learn to build a simple model
- Predict education outcomes from socioeconomic factors
- Split data into training and testing sets
- Evaluate model performance with basic metrics
- Interpret results: what do the predictions tell us?

## 🏗️ Mini-Deliverable

**Assignment:** Create a notebook with model results and a short written interpretation explaining "what does this mean?"

**Requirements:**
1. **Choose a social impact dataset** with a clear prediction target
2. **Build a simple predictive model** (decision tree or linear model)
3. **Split data properly** into training and testing sets
4. **Evaluate model performance** using accuracy or similar metrics
5. **Write a clear interpretation** explaining what the model predicts and why it matters
6. **Discuss limitations** and what the model might be missing

### Example Model Building:
```python
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, classification_report
import pandas as pd

# Load your social impact dataset
df = pd.read_csv('education_outcomes.csv')

# Define what we're trying to predict
X = df[['parent_education', 'household_income', 'school_resources']]  # Features
y = df['graduates_high_school']  # Target (1 = graduates, 0 = doesn't)

# Split into training and testing data
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=42
)

# Build a simple decision tree model
model = DecisionTreeClassifier(max_depth=3, random_state=42)
model.fit(X_train, y_train)

# Make predictions on test data
predictions = model.predict(X_test)

# Evaluate performance
accuracy = accuracy_score(y_test, predictions)
print(f"Model accuracy: {accuracy:.2f}")

# Interpret results
print("\\nModel Interpretation:")
print(f"The model correctly predicts graduation {accuracy:.1%} of the time")
print("\\nMost important factors for graduation:")

# Get feature importance (what the model thinks matters most)
feature_importance = pd.DataFrame({
    'feature': X.columns,
    'importance': model.feature_importances_
}).sort_values('importance', ascending=False)

print(feature_importance)
```

## 📁 Files Structure

```
week6/
├── README.md
├── notebooks/
│   ├── lecture_prediction_intro.ipynb
│   ├── tutorial_first_model.ipynb
│   └── assignment_prediction_project.ipynb
├── examples/
│   ├── education_prediction.ipynb
│   ├── health_outcome_model.ipynb
│   └── economic_forecasting.ipynb
├── data/
│   ├── social_impact_datasets/
│   └── example_predictions/
└── resources/
    ├── ml_interpretation_guide.md
    ├── model_evaluation_basics.md
    └── avoiding_common_mistakes.md
```

## 📖 Key Concepts Introduced

### Machine Learning Fundamentals (Non-Technical)
- **Supervised Learning**: Learning from examples to make predictions
- **Features**: The information we give the model (income, education, location)
- **Target**: What we're trying to predict (graduation, health outcome, poverty)
- **Training**: Teaching the model using historical data
- **Testing**: Checking how well the model works on new data

### Model Types (Focus on Understanding)
```python
# Decision Tree: Makes decisions like a flowchart
from sklearn.tree import DecisionTreeClassifier
model = DecisionTreeClassifier(max_depth=3)  # Keep it simple

# Linear Model: Finds straight-line relationships
from sklearn.linear_model import LogisticRegression
model = LogisticRegression()

# Training the model
model.fit(X_train, y_train)

# Making predictions
predictions = model.predict(X_test)
```

### Evaluation Basics
- **Accuracy**: What percentage of predictions were correct?
- **Precision**: Of the positive predictions, how many were actually positive?
- **Recall**: Of the actual positives, how many did we find?
- **Feature Importance**: Which variables matter most for predictions?

### Interpretation Guidelines
- Always explain predictions in the context of your social issue
- Discuss what the model can and cannot tell us
- Consider biases in the data and model limitations
- Focus on practical implications for policy or interventions

## 🎥 Video Resources

1. **Machine Learning for Social Good** (15 min)
2. **Building Your First Predictive Model** (25 min)
3. **Interpreting Model Results** (15 min)
4. **Common Pitfalls and How to Avoid Them** (10 min)

## 🌍 Social Impact Prediction Examples

### Education
- **Predict**: Student graduation likelihood
- **Features**: Socioeconomic status, school resources, attendance
- **Impact**: Target interventions for at-risk students

### Health
- **Predict**: Disease risk or health outcomes
- **Features**: Demographics, lifestyle, environmental factors
- **Impact**: Preventive care and resource allocation

### Economic Development
- **Predict**: Poverty status or income levels
- **Features**: Education, location, employment, infrastructure
- **Impact**: Policy decisions and aid distribution

### Environmental Justice
- **Predict**: Environmental health risks
- **Features**: Location, pollution levels, demographics
- **Impact**: Regulatory priorities and community interventions

## � Additional Resources

### Beginner-Friendly ML Resources
- [Scikit-learn User Guide](https://scikit-learn.org/stable/user_guide.html)
- [Machine Learning Explained](https://www.explainxkcd.com/wiki/index.php/1838:_Machine_Learning)
- [Google's AI for Everyone Course](https://www.edx.org/course/artificial-intelligence-for-everyone)

### Interpretation and Ethics
- [Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/)
- [Algorithmic Justice League](https://www.ajl.org/)
- [AI for Social Good](https://ai.google/for-social-good/)

## ❓ Common Questions

**Q: Do I need to understand the math behind machine learning?**
A: Not for this course! Focus on understanding what models do and how to interpret results.

**Q: How do I know if my model is good enough?**
A: Compare to simple baselines. If you can predict graduation with 75% accuracy vs. 50% random guessing, that's useful!

**Q: What if my predictions are wrong?**
A: All models are wrong, but some are useful. Focus on whether the insights help inform decisions.

**Q: How do I avoid bias in my models?**
A: Be aware of bias in your data, test on different groups, and always question your assumptions.

## 🆘 Getting Help

- **Discussion Forum**: Share datasets and model interpretation questions
- **Office Hours**: Tuesdays 6-7 PM
- **AI Assistants**: Great for explaining sklearn syntax and model interpretation
- **Peer Support**: Practice explaining model results to each other

## 📈 Assessment Criteria

Your prediction project will be evaluated on:
- **Model Implementation**: Code successfully builds and tests a predictive model
- **Performance Evaluation**: Appropriate metrics are calculated and reported
- **Interpretation Quality**: Clear, non-technical explanation of what the model shows
- **Social Context**: Discussion connects predictions to real-world impact
- **Limitations Discussion**: Honest assessment of what the model can and cannot do

---

**Next Week**: [Week 7: Automating Workflows with Functions + Using AI to Scale Code](../week7/README.md)

**Previous Week**: [Week 5: Working with External Data & APIs](../week5/README.md)
