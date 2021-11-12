
# README

## Evolution in time of the perception of events by social groups. Case studies.

### Abstract
Around events that attract global attention, any person is bound to state their opinion. Our goal is to visualise the evolution in time of the mindset of different personalities involved in an event, from close or afar, to potentially uncover patterns in human behavior. To successfully do this we distinguish classes among people, which can be achieved by considering the content of their speech. For this, we will use the dataset QuoteBank, which gathers millions of quotes of a large panel of public figures. By identifying keywords we can encapsulate the tone and a person’s feeling about an event or a situation. To get a more in depth understanding of the reason for the change in speech, the background and characteristics of the person are added to the dataset studied.
To put the results into perspective, the tone, publication of date and time of the articles in which the quote was cited are added to the dataset. 

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