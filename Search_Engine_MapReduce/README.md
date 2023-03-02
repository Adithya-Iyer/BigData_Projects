# Search Engine for Movie Plot Summaries

#### This project has been done using PySpark code that runs on a Databricks cluster.

We will work with a dataset of movie plot summaries that is available from the Carnegie Movie Summary Corpus site. We are interested in building a search engine for the plot summaries that are available in the file “plot summaries.txt” that is available here: http://www.cs.cmu.edu/~ark/personas/data/MovieSummaries.tar.gz

#### We use the tf-idf technique to accomplish the above task. For more details on how to compute tf-idf using MapReduce, see the links given in References section.

### Steps Involved:

1. Extract and upload the file plot summaries.txt from the given link to Databricks. Also upload a file containing user’s search terms one per line.
2. Remove stopwords and perform pre-processing.
3. Create a tf-idf for every term and every document (movie) using the MapReduce method.
4. Read the search terms from the search file and output following:
   * User enters a single term - output the top 10 documents with the highest tf-idf values for that term.
   * User enters a query consisting of multiple terms - evaluate cosine similarity between the query and all the documents and return top 10 documents having the highest cosine similarity values.
5. For the search terms entered by the user, you will return the list of movie names sorted by their relevance values in descending order. Return movie names, and not movie ID. Use the movie.metadata.tsv file to lookup the movie names.

Public URL of the notebook: https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/8864698106494585/400255745231741/1645558558670061/latest.html

### References:

* https://janav.wordpress.com/2013/10/27/tf-idf-and-cosine-similarity/
* https://sparkbyexamples.com/spark/spark-sparkcontext/
