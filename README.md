# Tweet-Sentiment-Extraction

![WhatsApp Image 2020-08-01 at 01 16 35](https://user-images.githubusercontent.com/52850825/89071607-b0059d80-d394-11ea-8a54-fdb41bec914f.jpeg)




### INTRODUCTION:
This project on Tweet Sentiment Extraction was a [Kaggle](https://www.kaggle.com/) competition.The task was to choose the text from within a given tweet which had labelled sentiments(Positive, Negative, Neutral), such that the selected text exemplifies the given sentiment.

Example: *Its a nice day*.

SENTIMENT: POSITIVE.

SELECTED TEXT:**nice**

**USING NER APPROACH**

We started by using a Named Entity Recognition approach.The technique it uses is that it filters out the string that **does not** reflect the polarity of the tweet.What's left is that part of tweet which is a better candidate to express the sentiment given.With this the type of tweet is extracted and mapped to the list of entity type.In the dataset the tweets with neutral sentiment had an average jaccard score of around 0.97(on a scale of 1).Hence in cases of neutral tweets, the entire tweet was considered as the selected text.For positive and negative sentiments we used different models.Accuracy obtained: **66.4%**

**QUESTION ANSWER MODEL USING RoBERTa**

This was our final approach towards the problem.We started with converting the data into arrays that roBERTa understands.This is achieved by gathering the input as a list of padded length.Tokens are given as input in the bert model and its embeddings are the first output.After adding a convolutional layer and reshaping the embeddings into desired shape, applying softmax and a little later training with 5 folds stratified KFolds, the best model weights are saved and then later reloaded when required.
Accuracy obtained: **70.3%**

### RESULTS:

**Public Leaderboard**

Score: 0.70391

Rank: 1515

**Private Leaderboard**

Score: 0.71252

Rank: 1313

### TEAM MEMBERS:

- **Gagan Aryan**

- **Nishima Panwar**

- **Tushar Singla**

- **Varenya Srivastava**

- **Yatish Goel**

### MENTOR:

- **Ishika Singh**

### TAKEAWAYS:

It was an excellent learning experience for the team, and a nice and detailed intro to the kaggle platform.In addition to the given task at hand our team ran a data analysis for the tweets having a jaccard score of less than 0.1 when predicted by our model.We predict around 9% of data to have its jaccard score in this bracket.Some inconsistencies were found as in the following examples:

Tweet:*Cool!!! No wonder you didn't sleep much*

Selected Text:**Cool!**.(Notice the single exclamation mark here as compared to three in the original text.)

Tweet:*So glad Sam is in good mood*

Selected Text:**good**

Selected by Model:**glad**.So here its just a matter of human choice to give preference of one word over another

***Note that in both the cases above the jaccard score would be 0.***

So not only this project made us realise the power of most modern of solutions to tackle an NLP problem, but it also gave us an opportunity to go beyond our constraints, in lines of keeping up with the spirit of research and enquiry. 

