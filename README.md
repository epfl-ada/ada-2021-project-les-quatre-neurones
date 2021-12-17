# README

## Projet Idea 

## Datastory 

You can find our datastory here: https://arthurbrousse.github.io/

## Notebooks

Our processing is splitted in 5 main notebooks for better modularity and parallel optimisation if needed, and correspond to the main steps of the analysis provided in the datastory 

### Data Processing 

This notebook is the first step of data processing for the enourmous quantity of data provided by quotebank. We select the columns that interest us in all of the data and imports it as a json, keeping the most attribute, being the Qids. It is then used in the scond part of this notebook, where we use this ID to gather information about the speaker and 

### Quote Extraction

This notebook comes second in the pipeline. It simply fetches quotes from the json.bz2 files (created in step above) from a selected list of keywords. These lists change for each year since new car models are released each year. The quotes are then saved to simple json files and transformed to pandas dataframes if further treatmen wants to be done in the same notebook by a user;

### Topic Analysis

This notebook reads the .json files of quotes from previous step and does a cleaning of the batches of quotes. Namely, it removes all special characters, punctuation and spaces from the quotes, then tokenises and removes stopwords from texts in list. For the latter part, NLTK's stopwords list is used. 
The next step is to remove quotes that are too similar. Indeed, some quotes are just substrings or reorderings of other quotes. In order to only keep the essential quote, the notebook builds a TF-IDF matrix using sklearn's TfidfVectorizer method. The similarity between quotes is assessed and we can proceed to selection. 

This way, the batch of quotes is reduced and topic analysis can be performed. This is done using gensim's LDA methods. Only one topic consisting of 6 words is computed for each month. This allows to identify events with words that are of more than ordinary interest. 

The words in the topics are then translate to cloud of words for visualisation.



### Emotional Pipeline

This notebook takes as an input the ones processed by the quotes extraction, and does not need the information of the topic. In essence, it will take these quotes, perform some baseline NLP, but as little as possible since we are doing sentiment analysis, which need detail in order to understand as much as possible the subtilities of the emotions conveyed by the sentence. Once the quotes are cleaned, they pass through 3 algorithms of emotion analysis: 

- VADER, the main one, is a lexicon based algorithm that outputs a compoud score that indicates the relative sentiment of the score, with -1 the most negative and 1 the most positive. We chose it as the main study tool since it outputs a continuous score which is easier to study. However, by analysing it manually we found discrepancies, sentences that were intepreted as negative by VADER but actually were quite positive. Therefore we decided to use another method as a support.
- BERT is a kind of neural network develloped for Natural Language Processing, which is based on a transformer network, that has been develloped and pre-trained for sentiment analysis. The difference with VADER is that it outputs a "review" score of a discrete value between 1 and 5, with 1 the lowest emotion score and 5 the highest. This already gives us quite a ground for analysis but when digging further, we noticed that they would sometimes give opposing scores. As a resut, we used a third algorithm as a confirmatory one.
- Text2Emotion is another python library that performs sentiment anlysis, but is more oriented towards precise emotions, but by associating them to their overall sentiment (i.e. Sad = Negative), we can use it as a tie-breaker in case of contrary results from VADER and BERT 

The vibe_check() function does exactly that, by cross checking the values of VADER, BERT and Text2Emotion, and correctif if needed. The correction it performs is that if VADER and BERT are in complete opposition, the emotion indicated by Text2Emotion breaks the tie, increasing or decreasing the VADER score if both BERT an the Text2Emotion went against it.

Following this analyis, we take advantage of the fact that the dataframes are already processed to analyse the distibutions of occupations of the speakers, and of other attributes that were of interest at some point 

### Plots 


------ Milestone 2 --------


# README

## Evolution in time of the perception of events by social groups. Case studies.

### Abstract


### Research Questions
- What information about the speaker's mindset does a quote convey about an event ? 
- Are there relevant “classes” that people could be sorted in ? Are they easily identifiable ? 
- Are there classes that are more prone to change their views before and after the event ? If yes, what are the most common patterns in the changes observed?

These research questions lead to underlying, more pragmatic problematics.
For example, we need to identify the emotions in a quote and the specific keywords that vehicle these emotions. This can be done through the use of external natural language processing APIs.

Another question is to which event is the quote related and what are the timestamps of the quote and the article compared to the event ?

A quote can be used in various contexts and the messages it vehicles either be supported or dismissed by the quoter. Using natural language processing again, we can identify the general feeling of the article towards the quote or the event described.

As a bonus : Another research question could to what extent do the words of some people influence the course of action, or does it work the other way round ? Which public figures tend to be the most influential ?

### Methods
In order to build an accurate method to analyse any new event and the way people’s minds vary about it, we need to start with known events and the people who commented on them. Additional information on these people is added and mandatory to define characteristic classes and identify if there is a correlation between their traits and their behaviour.

This eventually allows to pinpoint leads for keywords associated with differing views (as a simple example, the word “lies” would often appear in quotes of people against a certain person running for presidency).
We would need to filter common words such as coordinating conjunctions to not flood the relevant information. 

To facilitate the data analysis, we aim to build a database from the given quotebanks sub-dataset related to the event of interest and the wikidata dumps 
The database will resemble the following (diagram drawn according to crow’s foot notation). 

![alt text](https://github.com/epfl-ada/ada-2021-project-les-quatre-neurones/blob/master/DB_ER_diag_ADA.png?raw=true)

In order to get the database, some transformations are needed. We listed the ones we thought we could do for all the years, since for this milestone we did it mostly for the 2020’s dataset. 

Here are some of the data cleaning steps already followed for a first preparation of the database.
- Quotes: 
    - remove stop words (and, the, ...)
    - stemming and lemming the quotes
    - use NLTK function in order to categorize the words in the sentence for example
- Speakers: 
    - Keep the speakers that are not "None"
    - See if a person has multiple names and decide how we want to proceed.
    - Add features about the speakers using the file speaker_attributes.parquet
    - Find all the attributes that we need to complete the dataset (QIDS and labels)
- Date and quoteID:  
    - Keep only the relevant informations in the date or quoteID
- Remove columns that we don’t use

### Proposed Additional Datasets:
The provided speaker_attributes.parquet file gives us information about the speakers and will be essential for our project. The wikidata dumps would allow us to find interesting information about the different speakers. One of the most important points will be to be able to find the labels of the QIDS because even if these identifications are good to make our analyses, if we want to be able to interpret our results, we need their "definitions"/”meaning”.

### Proposed Timeline & Organisation with the team:

Week 9
- Strategy :
Take a first small but polarising event to develop a standard data analysis process adapted to our approach. First concentrate only on the public figures that have quotes related to the event. We will see if we have time to consider the “general public”. 

- Further data cleaning and transformation (Tatiana)

- DataBase (Bastien)

- Choice of events (Arthur) : Choose several other events, of various location and different scales (local, national, international) to study a large variety
Start GitHub.io

Emotion (Benjamin)
test how to apply NLTK to quotes and articles draw a basic list of emotions

Week 10
- Events selected: (all)
  - apply the tools developed the previous week 
  - Identify classes of people and cross check between events. 
  - Identify patterns in the evolution of behaviours
  - Improve sentiment analysis algorithm according to the events selected (Benjamin)

First ideas for data visualisation (Arthur) and documentation  

Week 11
- Check correlation between data and behaviours. (Benjamin, Tatiana)
- Start coding the website with the first case studies (Arthur, Bastien)
- add more complex case studies. (all)

Week 12
- All the case studies finished
- structure of the presentation finished
- Practical conclusions on the classes of people, the patterns of how the mindset changes and underlying factors.

Week 13

Finishing the website (all)
