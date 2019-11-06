
Parenting Styles and Depression:
Detecting depression-related cues in  posts from parents following different parenting styles


Introduction

Depression in new parents is a common problem.
1 in 7 women and between 2% and 25% of new fathers may experience PPD in the first year after postpartum. 
Since many studies have shown the harmful effects of parental depression on children, it is crucial to recognize postpartum depression during the well-child visits at the pediatrician.

But can pediatricians give parenting recommendations to lower the risks for a parental depression? 
In particular, analyzing two different parenting methods:
A more traditional approach, including sleep training the baby, and  Attachment Parenting, promoting maximal parental empathy and responsiveness, in combination with continuous bodily closeness and touch. Since Attachment Parenting requires more attention from the parents, this study is interested in analyzing if there are more depression-related cues in posts from attachment parents than in the post from parents following a more traditional parenting approach.

Depression-related subreddits are used to build a model to identify depression-related cues in posts.
The model is then used to predict the number of depression-related cues in text from traditional parenting subreddits, and a subreddit focused on attachment parenting.
With the results, the question of if one of the parenting methods shows more depression-related cues than the other is answered. The results are used to help pediatrics make recommendations on parenting philosophies.

Data collection

Using the Reddit API PRAW to download posts and post titles from the following Subreddits:

| Depression-related Subreddits | Number of Posts |
|-------------------------------|-----------------|
| postpartumdepression          | 178             |
| depression_help               | 999             |
| depression                    | 978             |
| total                         | 2155            |


| Control Subreddits | Number of Posts |
|--------------------|-----------------|
| AskHR              | 997             |
| HomeImprovement    | 993             |
| Advice             | 950             |
| organizing         | 203             |
| Total              | 3143            |


| Experiment Subreddits | Number of Posts |
|-----------------------|-----------------|
| sleeptrain            | 1000            |
| AttachmentParenting   | 905             |
| parenting             | 903             |
| DIY                   | 540             |


Since depression symptoms are related to sleep, and parenting groups discuss sleep, sleep-related terms are excluded from the model. ]Stop words: sleep, bed, night.

Depression-related data and control data are combined to one train data set, totaling 5298 observations.
Title and body are combined into one feature, including all text data.

Methodes

Sklearn is used to fit different models.  Multinomial Naive Bayes classifier and Counter Vectorizer for preprocessing were chosen for the end model.
The reason for choosing Counter Vecctorizer is that the model should be interpretable. With Counter Vectorizer, the number of times a word occurs in a document is counted and used for prediction. It is easy to look at the word frequency of the test data.

|                         | CVect/MNB |
|-------------------------|-----------|
| Train Score Accuracy    | 0.8973    |
| Test Score Accuracy     | 0.8906    |
| Test Score ROC_AUC      | 0.8979    |
| Test Sensitivity Score  | 0.9369    |
| Train Specificity Score | 0.8588    |


The model is used to predict the occurrence of depression-related cues in the parenting-related subreddits and one not parenting related subreddit as control.


Results

|                                                | Attachment Parenting | Sleep Train | Parenting | Control (DIY) |
|------------------------------------------------|----------------------|-------------|-----------|---------------|
| Percentage of Class depression-related Cues    | 37.24%               | 15.40%      | 31.89%    | 1.30%         |
| Average Probability of depression-related Cues | 38.23%               | 15.97%      | 32.27%    | 3.41%         |


Conclusion

There are significantly more depression-related posts in the Attachment Parenting Subreddit than in the Sleeptrain and the more 'traditional' Parenting subreddit.

This does not prove that parents who follow the Attachment Parenting style are more likely to develop depression than other parents. The differences in the speech could have many different reasons. It is, for example, possible that parents who consciously follow a specific parenting approach are more self-aware than other parents and, therefore, more likely do discuss struggles and emotions they are facing. It is also possible that parents who are at risk for developing depression are more likely to choose Attachment Parenting to raise their children.

Nevertheless, the differences in depression-related cues in speech are fascinating, and further investigation should be conducted.

It is immensely important that Pediatricians continue screening parents for signs of depression. It might be interesting to include questions regarding parenting styles into the screening process to gain more information about the relationship between parenting styles and depression.

References

https://www.postpartumdepression.org/resources/statistics/
http://www.thedoctorwillseeyounow.com/content/kids/art3549.html
https://www.healthychildren.org/English/ages-stages/prenatal/delivery-beyond/Pages/Dads-Can-Get-Postpartum-Depression-Too.aspx
https://well.blogs.nytimes.com/2010/09/08/new-parents-at-risk-for-depression/
