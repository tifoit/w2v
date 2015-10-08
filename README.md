# Building a Word2Vec Model with Twitter Data

## First install Python, numpy and Apache Spark 

Note: 

I.) Installing Anaconda installs Python, numpy, among other Python packages. If interested go here https://www.continuum.io/downloads

II.) to download Apache Spark go here: http://spark.apache.org/downloads.html

## Get the Repo

git clone https://github.com/castanan/w2v.git

cd /YOUR-PATH-TO-REPO/w2v 

## Edit 

Open tweets-to-w2v.py and replace the data path line (line 54)

datapath = '/Users/jorgecastanon/Documents/github/w2v/tweets.gz'

with your path:

datapath = 'YOUR-PATH-TO-REPO/w2v/tweets.gz'

## Generate the Word2Vec Model

Execute the following command

~/Documents/spark-1.5.1/bin/spark-submit tweets-to-w2v.py filter.txt

replacing with your Spark home path:

YOUR-SPARK-HOME/bin/spark-submit tweets-to-w2v.py filter.txt

Note: step 4 generates files myW2Vmatrix.npy and myWordList.npy that are used in Step 5 so you may want to check if they were generated

## Cluster Twitter Terms with K-means 

Execute the following command

~/Documents/spark-1.5.1/bin/spark-submit cluster-words.py

replace with 

YOUR-SPARK-HOME/bin/spark-submit cluster-words.py

Note: step 5 generates file myCluster.npy so you may want to check

We are ready to rock!


## NOTES:

a. All these script run in local mode and need to be change to cluster mode for running them with large data sets of tweets

b. A different list of keywords in filter.txt file may be useful for different applications

c. Larger amount of tweets (or text documents) are needed to get an accurate Word2Vec model 

d. The singular values of the Word2Vec matrix may be useful to choose the number of dimensions for each of the vectors associated with your terms, #âs and @âs 