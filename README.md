# README

## Datastory 

You can find our datastory here: https://arthurbrousse.github.io/

## Notebooks

Our processing is splitted in 5 main notebooks for better modularity and parallel optimisation if needed, and correspond to the main steps of the analysis provided in the datastory 

### Data Processing 

This notebook is the first step of data processing for the enormous quantity of data provided by Quotebank. We select the columns that interest us in all of the data and imports it as a json, keeping the most attribute, being the Qids. It is then used in the second part of this notebook, where we use this ID to gather information about the speaker and 
 
### Quote Extraction

This notebook comes second in the pipeline. It simply fetches quotes from the json.bz2 files (created in the above step) from a selected list of keywords. These lists changes for each year, since new car models are released each year. The quotes are then saved to simple json files and transformed to pandas dataframes, if further treatmen wants to be done in the same notebook by a user.

### Topic Analysis

This notebook reads the .json files of quotes from previous step and does a cleaning of the batches of quotes. Namely, it removes all special characters, punctuation and spaces from the quotes, then tokenises and removes stopwords from texts in list. For the latter part, NLTK's stopwords list is used. 
The next step is to remove quotes that are too similar. Indeed, some quotes are just substrings or reorderings of other quotes. In order to only keep the essential quotes, the notebook builds a TF-IDF matrix using sklearn's TfidfVectorizer method. The similarity between quotes is assessed and we can proceed to selection. 

This way, the batch of quotes is reduced, and topic analysis can be performed. This is done using gensim's LDA methods. Only one topic consisting of 6 words is computed for each month. This allows us to identify events with words that are of more than ordinary interest. 

The words in the topics are then translated to clouds of words for visualisation.

### Emotional Pipeline

This notebook takes as an input the ones processed by the quotes extraction, and does not need the information of the topic. In essence, it will take these quotes, perform some baseline NLP, but as little as possible since we are doing sentiment analysis, which need detail in order to understand as much as possible the subtilities of the emotions conveyed by the sentence. Once the quotes are cleaned, they pass through 3 algorithms of emotion analysis: 

- VADER, the main one, is a lexicon based algorithm that outputs a compound score that indicates the relative sentiment of the score, with -1 being the most negative and 1 the most positive. We chose it as the main study tool since it outputs a continuous score which is easier to study. However, by analysing it manually, we found discrepancies, sentences that were intepreted as negative by VADER but actually were quite positive. Therefore we decided to use another method as a support.
- BERT is a kind of neural network developed for Natural Language Processing, which is based on a transformer network, that has been developed and pre-trained for sentiment analysis. The difference with VADER is that it outputs a "review" score of a discrete value between 1 and 5, with 1 the lowest emotion score and 5 the highest. This already gives us quite a ground for analysis but when digging further, we noticed that they would sometimes give opposing scores. As a result, we used a third algorithm as a confirmatory one.
- Text2Emotion is another python library that performs sentiment analysis, but is more oriented towards precise emotions, by associating them to their overall sentiment (e.g. Sad = Negative). We can use it as a tie-breaker in the case of contrary results from VADER and BERT 

The `vibe_check()` function does exactly that, by cross checking the values of VADER, BERT and Text2Emotion, and correct if needed. The correction it performs is that if VADER and BERT are in complete opposition, the emotion indicated by Text2Emotion breaks the tie, increasing or decreasing the VADER score if both BERT and the Text2Emotion went against it.

Following this analysis, we take advantage of the fact that the dataframes are already processed to analyse the distibutions of occupations of the speakers, and of other attributes that were of interest at some point.

### Plots 

This notebook centralises the informations and functions used to plot the different informations outputed by the different previous notebooks. All the plots in this one are performed using plotly for more interactive graphs, and the static one like the wordclouds are directly plotted in the notebooks that process their corresponding informations. 
