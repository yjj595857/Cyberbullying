# Investigating-Cyberbullying-Using-Network-and-Textual-Analytics
Cyberbullying is a serious and prevalent issue. It impacts nearly 25% of all teens in America, and has serious impacts.
We chose to focus on Twitter because it has text and aggregate network features.
Our original plan was to use Twitter API to collect timelines of tweets from randomly sampled public accounts.
But we could not scrape our own data, so we settled for a 2013 Wikipedia Comments dataset found on Github. This data was collected by 
polling Twitter’s API for random account IDs, so each row represents an unique account, with information like handle, 
followers, following and statuses count and their last tweet. Because the nature of cyberbullying is directed, we filtered
for such tweets, and were left with around 30,000 usable tweets.

We first classified which tweets were instances of cyberbullying. This was a challenging problem as hand-labelling was not a 
viable option. Taking reference from the paper, we adopted a transfer approach, whereby a classifier is trained on labelled 
data from another platform and applied to unlabelled data of this platform. We then worked with a labelled dataset of 
wikipedia comments. After preprocessing the data we obtained n-grams of the text using gensim.
We chose the Complement Naive-Bayes model as it yielded good overall accuracy and precision and can better handle imbalanced 
datasets. 

We analyzed the textual features and network features. In the network features, we randomly sampled 200 out of 2900 comments to observe the graph structure. It turns out that the network is very peripheral, and few nodes have many edges within the network, which means that among people who post bullying content, only few of them target multiple subjects.
We also ran a T-test to identify the statistical difference between bulliers and non-bulliers. It shows that only the statuses count, which is the number of tweets, is significantly different between the two groups. But we can see that the bullying group is more active on the platform, since they have on average more followings and followers.
For textual features, we applied LIWC to compare textual features between Wikipedia comments and twitter. For both platforms, the bullying comments are much more negative. But for the Wikipedia comments, the scores are much higher, probably because on average each comment is longer than each tweet.

We identified some limitations and further improvements. First, there was a lot of false positives. On the left are actual toxic comments, but on the right are wrongly identified comments. Second, the similarity score between two datasets is only 68%. We need to get data from other social platforms to increase performance of our classifier.
Besides, because we only had one tweet from every account, we do not have enough historical data to identify that person as a “cyberbully”. Last, we found the network of bullying is very dispersed, so we cannot apply robust network analytic tools.
We hope to obtain a larger, well-structured data on social media for future improvements, to explore more features and more relationships of cyberbullying. We also listed some questions that future research could try to answer.

