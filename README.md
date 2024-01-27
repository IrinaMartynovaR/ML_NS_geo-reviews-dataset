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
We have implemented several baseline models; please see details in the paper.

*Accuracy* is the base metric for all tasks evaluation. For some tasks, additional metrics are used:
- **RuMedTop3** and **RuMedSymptomRec** - *Hit@3*
- **RuMedNER** - *F1-score*

Test results:

| Model | RuMedTop3 | RuMedSymptomRec | RuMedDaNet | RuMedNLI | RuMedNER  | ECG2Pathology | RuMedOverall |
| ------ | :------: | :------: | :------: | :------: | :------: | :------: | :------: |
|Naive | 10.58/22.02 | 1.93/5.30 | 50.00 | 33.33 | 93.66/51.96 | 1.15 | 29.53 |
|Feature-based | **49.76/72.75**  |  32.05/49.40  |   51.95 |  59.70  | 94.40/62.89 |  -  | 58.46 |
|BiLSTM | 40.88/63.50  |  20.24/31.33  |   52.34 |  60.06  | 94.74/63.26 |  -  | 53.87 |
|RuBERT | 39.54/62.29 | 18.55/34.22 | 67.19 | 77.64 | 96.63/73.53 | - | 61.44 |
|RuPoolBERT | 47.45/70.44 | 34.94/52.05 | 71.48 | 77.29 | 96.47/73.15 | - | 67.20 |
|RuBioBERT* | 43.55/68.86 | 28.94/44.55 | 53.91 | 80.31 | 96.63/75.97 | - | 62.69 |
|RuBioRoBERTa* | 46.72/72.87 | **44.01/58.95** | 76.17 | 82.77 | **97.19/77.81** | - | **71.54** |
|Human | 25.06/48.54 | 7.23/12.53 | **93.36** | **83.26** | 96.09/76.18 | 39.34 | 58.13 |
