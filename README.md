# Data-Mining
EXPLORATORY DATA ANALYSIS AND CLASSIFICATION OF NETFLIX CONTENT
Prepared By:	ID
1.	Yafet Adinew	DTU14R0136
2.	Chilotaw Amare	DTU14R0518
3.	Aysheshim Aynetaw	DTU14R0660
4.	Demisew Yitayaw	DTU14R0244
5.	Asmamaw Mehari	DTU14R0238


. Conclusion & Discussion
8.1 Summary of Findings
The project successfully achieved both primary and secondary objectives:
1.EDA Insight: The analysis confirmed the Netflix library is 69% Movie-dominant and demonstrated that content acquisition peaked in 2019-2020.
2.Predictive Success: The simple Decision Tree Classifier, utilizing just three features ('duration_value', 'rating_enc', 'year_added'), achieved a phenomenal Accuracy of 99.89% and a F1-Score of 0.9992.

8.2 Critical Discussion: The Issue of Data Leakage
The near-perfect performance of the model must be critically evaluated. In machine learning, such results are often indicative of a data leak or a trivial classification scenario.
Trivial Solution: The high performance is a direct result of the feature 'duration_value'. This feature contains values in 'minutes' (for Movies) and 'seasons' (for TV Shows). The Decision Tree simply identified a single, perfect split (e.g., "If 'duration_value' is greater than 20, predict Movie; otherwise, predict TV Show").

Proxy Variable: The 'duration_value' column is not a predictive feature but a direct proxy for the target variable ('type') itself. The classification task was reduced to identifying the unit of measurement used in the 'duration' column, not learning subtle patterns from independent metadata.
While demonstrating perfect execution of the data pipeline and model training, the result highlights that the problem, as defined by the current features, is trivially solved and does not represent a challenging learning task for the algorithm.
8.3 Potential Improvements and Future Work
To ensure the model is truly learning and generalising from independent features, future iterations must pursue the following advanced steps:
1.Feature Re-Selection (Addressing Leakage): The 'duration_value' feature must be excluded from the feature set. The classification task should then be attempted using only the remaining independent features ('rating_enc', 'year_added') plus the features that were previously excluded.
2.Advanced Feature Integration: Implement encoding techniques for the high-cardinality features that carry rich information:
Genre ('listed_in'): Use One-Hot Encoding or Binary Encoding to incorporate the top 20 genres.
Country ('country'): Use Target Encoding or Frequency Encoding to incorporate the country of production, which is a strong independent predictor of content type.

3.Model Robustness: For the new, more challenging classification task (without 'duration_value'), the model should be upgraded to a more robust Ensemble Method like Random Forest or XGBoost, which can better handle feature interactions and prevent overfitting on complex data.

