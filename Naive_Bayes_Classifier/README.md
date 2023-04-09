# Naïve Bayes Classifier

#### This project has been done using PySpark code that runs on a Databricks cluster.

We will use Spark based MapReduce algorithm to identify messages that are not spam (or ham, in other words). The dataset for this task is available here: [http://www.cs.cmu.edu/~ark/personas/data/MovieSummaries.tar.gz](https://archive.ics.uci.edu/ml/datasets/sms+spam+collection)

#### The Naïve Bayes classifier is trained from scratch. It is important to note that only unigram probabilities are used and there is a class imbalance in the dataset as well.

### Steps Involved:

1.  Separates each row of the data by splitting it on the tab character (\t).
2.	Tokenizes the text by converting it to lowercase and using the wordpunct_tokenize function from the nltk library.
3.	Removes English stop words and punctuation marks from the tokenized text.
4.	Stems each word in the tokenized text using the PorterStemmer algorithm.
5.	Splits the preprocessed data into training and testing sets.
6.	Calculates the prior probability of each category (spam or ham) in the training set.
7.	Calculates the conditional log probability of each word given each category in the training set.
8.	Uses the Naïve Bayes algorithm to classify each message in the test set as either spam or ham.
    *	Naïve Bayes defines the joint conditional probability as just the product of individual conditional probabilities.
    *	Since we take log probability in order to avoid extremely small products, we add the log values.
    *	After finding the conditional probabilities for each class for a given sample, we return the class with most likelihood.
9.	Calculates the performance metrics of the classifier (accuracy, precision, recall, and F1-score) using the confusion matrix.


Public URL of the notebook: [https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/8864698106494585/400255745231741/1645558558670061/latest.html](https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/8864698106494585/567179378413741/1645558558670061/latest.html)

### References:

* https://archive.ics.uci.edu/ml/datasets/sms+spam+collection
* https://sparkbyexamples.com/spark/spark-sparkcontext/
