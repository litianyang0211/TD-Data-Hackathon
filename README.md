# TD Rotman FinHub TDMDAL Hackathon

## Task
In this project, we developed a ML process extracting information from the transcript of **earning calls** to predict stock price movement (**net return**) on the next trading day.

## Available Data
Records of quaterly earning calls which are provided as paragraphs(.json) and daily stock returns(.csv) from Feb.2013 to Feb.2020 for 464 listed U.S. companies.

## Methodology
1. We splitted each transcript into the **manager discussion** and **Q&A** parts because they are different in nature.
2. For each part, we measured the emotions using a **Loughran McDonald dictionary** and a **finance terminology dictionary**. Number of words in different categories(positive, negative, uncertain...) are counted which forms input data to following algorithms.
3. **Random forests**, **support vector regressions**, and **XGBoost** are used to predict returns.
4. **Five-fold cross validation** is implemented to find the best configuration(hyperparameters) and model.
5. Raw predictions on test set are scaled so that they have the same variance as the training set.

## Outcome
1. The number of negative words in **Q&A** part had quite **different** distribution than that in **manager discussion** part.
2. Scaling raw predicted distribution effectively increased prediction accuracy.
3. Random forest worked best among the three models. It has a **55% accuracy** in predicting stock price directions and a mean square error of **0.0016**(30% less than linear regression) in predicting returns.
