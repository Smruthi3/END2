## Building Sentiment Classifier using LSTM

### Data Overview 

Data from the StanfordSentimentAnalysis Dataset is considered to build the LSTM Model 

Based on Readme file given by StandordSentiment Treebank, the following way sentence and sentiment label are mapped

	1. datasetSentences.txt contains sentence and corresponding index
	2. datasetSplit contains the sentence index and splitset label. Splitset labels 1,2,3 corresponds to tarin, test and dev respectively
	3. datasetSentences and datasetSplit merged based on sentence index. let's call it as merged_dataset
	4. sentiment_labels contains phrase id and sentiment values ranging from 0 to 1. Here notice that there is no one to mapping between datasetSentences and sentiment_labels
	5. dictionary.txt contains all phrases and their IDs
	6. Now, perfom left join on merged_dataset and dictionary using sentence and phrases
	7. As we have phrase id, again perform left join on previous dataset (obtained from step #6) and sentiment_labels using phrase_id and phrase id
	8. Here we get a final table with sentiment values
	9. Divide the sentiment values into 5 buckets [0, 0.2], (0.2, 0.4], (0.4, 0.6], (0.6, 0.8], (0.8, 1.0] and assign a label from 0 to 4
	10. Finally, use a split label to devide your data into train,test and dev 

### Data Augmentation

The following augmentation techniques are tried:

** Back Translation **

Intially tried for all the sentences in the training data set. It look lot of time but did not convert more than few sentences so for the demonstartion purpose the below mentioned approuch is used

Due to following limitations of the package only a random smaple of 10 sentences (why 10 just randonly chosen) are taken and performed this augmentation. Germen language is chosen here (one can choose multiple langauges too)

	1. The maximum character limit on a single text is 15k.
	2. Due to limitations of the web version of google translate, this API does not guarantee that the library would work properly at all times
	   If there is time, probably back transaltion can be done on entire training set by passing sentences in multiple batches on different days/time


** Radom swap **

The random swap augmentation takes a sentence and then swaps words within it n times, with each iteration working on the previously swapped sentence. Here we sample two random numbers based on the length of the sentence, and then just keep swapping until we hit n.

	1. This function takes words list as one of the arguments. So sentences are splits based on spaces and passed 
	2. Function returns the randomly swapped words in a list later is combined as a sentence
	
** Random Deletion **

As the name suggests, random deletion deletes words from a sentence. Given a probability parameter p, it will go through the sentence and decide whether to delete a word or not based on that random probability. 

	1. This function takes words list as one of the arguments. So sentences are splits based on spaces and passed 
	2. Function returns the randomly deleted words in a list later is combined as a sentence
	
Note that, all the three methods are applied only on training data set separately and combined as a single data set 



