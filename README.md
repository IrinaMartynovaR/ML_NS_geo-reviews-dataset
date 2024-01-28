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
|LogisticRegression | **0.78**  |  3min 13s  |
|CatBoost | 0.78  |   41min 31s  |
|LSTM | 0.79  |   33min 17s  |
|CNN | 0.75  |   1h 17min 17s  |
|RuBERT | 0.26 | 7h 26min 54s | 
|rubert-tiny2 | **0.83** | 4h 12min 04s |
|rubert-tiny2-one_BertLayer* | 0.81 | **9min 24s** |
|rugpt3small-two_GPTLayer** | 0.79 | 3h 2min 13s |

*all layers were removed, leaving only one

**all layers except two were removed, and the [Sophia](https://arxiv.org/abs/2305.14342) optimizer was used to improve quality.

To enhance the accuracy of ML methods, additional features were created.


In the 'Feature_engineering' file, additional features were added to enhance the accuracy of machine learning methods. Here's a summary of the actions taken in the code:

    1.Noun, Adverb, and Adjective Counting:
        The code defines functions (count_nouns, count_adverbs, count_adjectives) to count the number of nouns, adverbs, and adjectives in each text entry of a DataFrame. 
        
    2.Punctuation and Uppercase Letters Counting:
        The code calculates the count of specific punctuation and uppercase letters in each text entry and adds these counts as new columns (specific_punctuation_count and
        uppercase_letters_count) to the DataFrame.

    3.Word Frequency Analysis:
        The code calculates the frequency of each word in the text data and identifies rare and frequent words. The thresholds for rare and frequent words are defined, and 
        new columns (rare_words and frequent_words) are added to the DataFrame based on these thresholds.

    4.Top Words by Class:
        The code reads a CSV file and performs additional analysis to identify the top words for each class ('Positive', 'Neutral', 'Negative'). The top words for each class 
        are stored in the top_words_by_class dictionary.

    5.Filtering Specific Words:
        The code filters out the first 50 common words from the positive, neutral, and negative classes. The remaining 15 words are considered specific to each class. These specific
        words are then used to create new binary columns (pos_f, negat_f, neut_f) indicating the presence of specific words in each text entry.

