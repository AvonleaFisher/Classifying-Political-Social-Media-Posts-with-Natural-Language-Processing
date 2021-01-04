# Classifying Political Social Media Posts with Natural Language Processing

## Introduction 
This project aims to create two classification models for political social media posts. The first is a binary classifier to predict whether the posts are partisan or neutral. The second is a multiclass model that predicts the overall message category of a post. The data used for this project is Crowdflower's 2015 [Political Social Media Posts dataset](https://www.kaggle.com/crowdflower/political-social-media-posts), which contains Facebook and Twitter posts from politicians' accounts, as well as human-labeled variables such as the post's bias and the substance of its message. There are 5000 total posts and 21 columns in the dataset. The ability to classify the bias and message of politicians' posts can help constituents, political organizations, and research institutions better understand their political views.

## Methods
Word clouds, word frequency plots, and bigram plots were used to explore the most common words/word pairings in subsets of the data. 
The social media posts were cleaned and then numerically encoded using TDF-IDF. The dependent variables, bias and message, were dummy encoded 
and label encoded, respectively. 

Due to extreme class imbalance, models were trained on balanced data that was sampled using the Synthetic Minority Oversampling Technique (SMOTE). A random forest model was created and optimmized for the bias classification task. A K-Nearest Neighbors model was optimized for classifying the posts' message. 

The models were used to make predictions on a new, small sample of Tweets collected using Tweepy and Twitter's API.

## Results
The confusion matrices below provide a visual overview of the performance of the models on test data:

![Test](https://github.com/AvonleaFisher/Classifying-Political-Social-Media-Posts-with-Natural-Language-Processing/blob/master/images/Model%20Performance.png)

The Random Forest classifier had 91% accuracy and the KNN classifier had 87% accuracy. 

## Recommendations 
The random forest model can be used to predict whether a social media post is partisan or neutral with high accuracy. After collecting Tweets or other social media posts for more recent data, partisan posts can be identified and extracted for review by constituents or organizations interested in learning more about a particular politician’s views.

The KNN model can classify the message of a post with significantly higher accuracy than random guessing, and performs particularly well on the following classes: attack, constituency, media, mobilization, and ‘other’. The exploratory analysis suggested that posts perceived as partisan tend to contain words/word pairings related to specific policy or legislative issues, like ‘law’, ‘health care,’ and ‘immigration reform.’ These terms can be used in queries when attempting to collect partisan posts.

## Limitations and Next Steps
Future work should test and optimize different model types, particularly for the message classification task. Given the age of this dataset, it may also be fruitful to collect and label more recent data of a similar type. With such data, future work could assess how the distribution of classes has changed since 2015.
