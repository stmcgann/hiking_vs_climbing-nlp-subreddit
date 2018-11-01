# hiking_vs_climbing-nlp-subreddit
Use pushshift API to capture thousands of subreddits in 'climbing' and 'hiking'. Performed NLP to predict whether subreddit originated from 'climbing' or 'hiking'. 

This project focuses on posts captured from 2 subreddits: hiking and climbing. Through testing two vectorzing techniques (Count Vectorizer and TF-IDF) and three statistical models (Random Forest Classifier, Extra Trees Classifier, and Naive Bayes (Multinomial)), this analysis predicts where a subreddit post was published (hiking or climbing). Analysis and modeling for this task proved interesting for 2 key reasons:

1. While technically distinct, the topics of hiking and climbing share themes, standard vernacular, and subreddit participants (participants = authors and commenters). 
2. Many of these posts are picture intensive, making the process of NLP more challenging. (Important note: a second installment to this project will soon be available on https://stmcgann.github.io/ where the same posts are analyzed using Neural Networks. Instead of focusing on the text attributes of each post, the analysis will be based solely on analysis of the pictures that accompany each post). 
Using a publically available pushshift API, 3974 climbing posts and 2312 hiking posts were captured and saved into separate data frames. Each data frame captured the same 9 features ('title', 'selftext', 'subreddit', 'created_utc', 'author', 'num_comments', 'score', 'is_self') so they could easily be concatenated into a single data frame. The final data frame ('df') contains 6286 rows and 10 features. The additional feature, 'text_concat', is the combination of the 'title' and 'selftext' feature; 'text_concat' is the feature that was vectorized in this notebook.

Two tree methods (Random Forest Classifier and Extra Tree Classifier) and one regression metric (Multinomial Naive Bayes) were used on the subreddit data. The Multinomial Naive Bayes model with the count vectorizer resulted in the best performing model, classifying the correct subreddit 95.3% of the time on my testing data set. Further, out of the 6286 posts, the Naive Bayes model only falsely predicted hiking 27 times and falsely predicted climbing 32 times on the test data. On the test data, the Naive Bayes model correctly predicted climbing 768 times and correctly predicted hiking 431 times.

   1. False Positives: 27
   2. False Negatives: 32
   3. True Negatives: 768
   4. True Positives: 431
   
In analyzing the best performing Random Forest model, the top 10 most predictive, non-lemmatized words were: 'hiking', 'climbing', 'hike', 'trail', 'hikes', 'trails', 'climb', 'climber', 'boots', 'climbers'.
