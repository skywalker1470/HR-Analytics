# HR Recruitment Intelligence Analysis

An end to end HR analytics project built on the IBM HR Analytics Employee Attrition and Performance dataset. The notebook covers data preprocessing, exploratory data analysis, statistical hypothesis testing, predictive modeling, and actionable workforce insights.

## Project Structure

- `HR_Analytics_IBM_Dataset.ipynb` the main analysis notebook
- `data.csv` the IBM HR Analytics dataset (1,470 employee records, 35 columns)

## Objective

Analyze employee attrition patterns to identify the strongest drivers of turnover and build predictive models that flag at risk employees, supporting data driven HR and retention decisions.

## Dataset

The dataset contains employee level records including demographics (Age, Gender, MaritalStatus), job details (Department, JobRole, JobLevel, OverTime), compensation (MonthlyIncome, DailyRate, PercentSalaryHike), satisfaction scores (JobSatisfaction, EnvironmentSatisfaction, WorkLifeBalance, RelationshipSatisfaction), and tenure metrics (YearsAtCompany, YearsSinceLastPromotion, YearsWithCurrManager). The target variable is `Attrition` (Yes/No).

## Workflow

1. **Data Loading and Cleaning** drop constant and redundant columns (`EmployeeCount`, `Over18`, `StandardHours`, `EmployeeNumber`), check for nulls and duplicates
2. **Exploratory Data Analysis** attrition overview, demographics vs attrition, satisfaction scores, tenure and promotion patterns, and a full correlation heatmap
3. **Statistical Hypothesis Testing** Mann Whitney U tests for continuous variables, Chi square tests for categorical variables, and point biserial correlation for effect sizes
4. **Feature Engineering** composite risk indicators such as SatisfactionScore, CareerStagnation, IncomePerYear, and PromotionLag
5. **Predictive Modeling** Logistic Regression and Random Forest classifiers, evaluated with cross validation
6. **Model Evaluation** confusion matrices, ROC and precision recall curves, feature importance, and coefficient/odds ratio analysis
7. **Cohort and Time Series Analysis** simulated recruitment KPIs (hires, exits, time to fill, offer acceptance rate) and cohort retention curves

## Key Findings

- Overall attrition rate is approximately 16%
- Sales has the highest attrition rate; R&D the lowest
- Employees working overtime are about 2x more likely to leave
- Single employees show higher attrition than married employees
- Junior roles (Job Level 1) show roughly 3x higher attrition than senior levels
- Attrition peaks in the first 0 to 2 years of tenure and again after 6+ years without a promotion
- OverTime, JobSatisfaction, WorkLifeBalance, YearsSinceLastPromotion, and MonthlyIncome are all statistically significant predictors of attrition (alpha = 0.05)

## Model Performance

| Metric | Logistic Regression | Random Forest |
|--------|---------------------|----------------|
| Accuracy | ~78% | ~85% |
| ROC AUC | ~0.81 | ~0.90 |

Random Forest is the recommended model based on these results.

## Recommendations

1. Cap mandatory overtime and introduce comp time programs
2. Create lateral growth paths for employees who have gone 3+ years without a promotion
3. Deploy quarterly pulse surveys and trigger interventions when satisfaction scores fall below 2.5
4. Invest in structured onboarding and mentorship during the first 18 months of employment
5. Review compensation for lower job levels earning under $3k per month
6. Offer remote work flexibility for frequent travelers

## Tech Stack

- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- SciPy (statistical testing)
- Scikit-learn (Logistic Regression, Random Forest, model evaluation)

## Getting Started

1. Install the required packages:
   ```
   pip install pandas numpy matplotlib seaborn scipy scikit-learn
   ```
2. Open `HR_Analytics_IBM_Dataset.ipynb` in Jupyter or VS Code
3. Run all cells in order; `data.csv` must be in the same directory as the notebook
