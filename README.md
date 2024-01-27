![Python 3.8](https://img.shields.io/badge/python-3.8-green.svg)

# Geo Reviews Dataset 2023
Dataset Description:

    500,000 unique reviews
    Reviews exclusively for organizations in Russia
    Available on Yandex Maps
    Published from January to July 2023
    The dataset excludes short single-word reviews
    Texts are cleansed of personal information (phone numbers, email addresses)

Dataset Composition:

The dataset in tskv format includes the following information:

    Organization's address (address)
    Organization name (name_ru)
    List of categories to which the organization belongs (rubrics)
    User rating from 0 to 5 (rating)
    Review text (text)


## Baselines & Results
We have implemented several baseline models; 

F1-weighted is the base metric for evaluating the balanced precision and recall in multi-class classification tasks, providing a harmonized measure that considers the impact of class imbalance on overall model performance

Test results:

| Model | F1-weighted | time |
| ------ | :------: | :------: |
|MultinomialNB | 0.75 | **3.98 s** | 
|SVM | 0.77 |  2min 58s  | 
|LogisticRegression | 0.78  |  3min 13s  |
|CatBoost | 0.78  |   41min 31s  |
|LSTM | 0.79  |   33min 17s  |
|CNN | 0.75  |   1h 17min 17s  |
|RuBERT | 0.26 | 7h 26min 54s | 
|rubert-tiny2 | **0.83** | 4h 12min 04s |
|rubert-tiny2-one_BertLayer | 0.81 | **9min 24s** |
|rugpt3small-two_GPTLayer | 0.79 | 3h 2min 13s |
