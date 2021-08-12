# Sentiment-Analysis

Performing sentiment analysis on IMDB movie review dataset. It contains many positive and negative reviews on movies. 

The data set can be downloaded from:  http://ai.stanford.edu/~amaas/data/sentiment/

## Preprocessing the Data

Preprocessing involves cleaning the data before it can be used for NLP. The preprocessing steps performed on this dataset are: 
* The dataset is converted into lowercase.
* Each review is stripped of any trailing white spaces.
* Special characters and line breaks are removed from data.
* Stop words are removed from the dataset as they are not required for analysis and training.
* Total number of unique words i.e. the vocabulary of the training data is determined and buffer value of 50 words are added to it.
* Then vectorization is applied on data. It involves converting the text into equivalent numerical values. This is performed using one hot encoding.
* This data is further trained and encoded by the embedding layer of the CNN algorithm used.

## NLP Model

Using CNN for text analysis gives an advantage as CNN algorithms also consider the spatial information of the input to train and evaluate the values. By representing each word with a vector of numbers of a specific length and stacking words on top of each other, we get an “image.” The CNN network used has the following layers:
* Embedding layer: The embedding layer initializes with random weights and learns the embedding of all the train set words. In the model used, the parameters provided to the 
embedding layer are- vocabulary as calculated for train data, vector space or the output dimension of 20, and input length of 2000. The output of the Embedding layer is a 2D vector with one embedding for each word in the input sequence of words.
* Dropout layer: Dropout layer drops random nodes at the rate of 20% as given in parameters. It prevents overfitting as well as reduces the number of parameters to be trained.
* Conv1D layer: This convolutional layer has 32 feature maps and reads embedded word representations 3 vector elements of the word embedding at a time. Valid padding is used. 
* GlobalMaxPooling1D: The convolutional layer is followed by a 1D max pooling layer.
* This is followed by a dense layer of 250 neurons and a dropout layer.
* The output layer used is dense layer with 2 neurons as the dimension of output is 2. 
* Loss function used is binary crossentropy, optimizer used is Adam. 
