# Friend Recommendation using Mutual Friends

#### This project has been done using PySpark code that runs on a Databricks cluster.

We will use Spark based MapReduce algorithm to generate friend recommendation for users. The recommendations will be based on number of mutual friends. The dataset for this task is available here: http://www.cs.cmu.edu/~ark/personas/data/MovieSummaries.tar.gz

#### We use the a BFS-based approach, where every user at a distance of 2 from a user is a potential suggestion, and then these are ranked based on how many level 1 connections are responsible for the existence of a mutual relationship/acquitance.

### Steps Involved:

1.  Reads in a file containing information about friends in a social network (stored in a text file in a distributed file system).
2.	Processes the input file by splitting each line into a list of strings (using tab as delimiter) and filtering out any lines where the second element (representing a list of friends for a user) is empty.
3.	Further processes the filtered input data by splitting the list of friends for each user into individual friend connections, and creating a new RDD where each row contains a pair of users who are friends.
4.	The RDD created in the previous step is used to create a reverse mapping where each row contains a pair of users who are friends in reverse order.
5.	Joins the two RDDs created in the previous steps to obtain mutual friends for each pair of users.
6.	Counts the number of mutual friends for each pair of users and creates a new RDD where each row contains a pair of users and the number of mutual friends they have.
7.	Extracts the first user from the RDD created in step 3 and creates a new RDD where each row contains the second user and -1.
8.	Subtracts the RDD created in step 7 from the RDD created in step 6 to obtain a new RDD containing only the pairs of users for which there are mutual connections (i.e., excludes pairs where one user has no friends).
9.	Creates a new RDD where each row contains a user and a tuple containing the ID of one of their friends and the number of mutual friends they share.
10.	Groups the RDD created in step 9 by user ID and selects the top 10 friend recommendations for each user based on the number of mutual friends.
11.	Generates output in the form of a tab-separated file containing each user's ID and a list of their top 10 recommended friends (based on mutual connections).
12.	Saves the output file in a distributed file system.

Public URL of the notebook: https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/8864698106494585/400255745231741/1645558558670061/latest.html

### References:

* https://an-ml.s3.us-west-1.amazonaws.com/soc-LiveJournal1Adj.txt
* https://sparkbyexamples.com/spark/spark-sparkcontext/
