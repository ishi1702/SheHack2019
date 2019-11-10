# SheHack2019
### CETO
**Disaster Management App**

#### Introduction:
Our country has continuously suffered from the devastations caused by many calamities which claimed a huge loss of life and economy. India has faced 649 disasters from 1915 to 2019. Out of these 649 events, 302 disasters were caused by flood on an average of 3 floods per year. The rescue and relief activities during these times faced a lot of challenges in trying to curb the magnitude of the disaster. 
Hence, we propose a web application to organise a more feasible and efficient rescue operation during environment and sustainable development challenges. 
This web application deals with three major aspects:
1. It checks the location, time of the tweet.
1. It checks the common keyword used in tweets and retweets.
1. Focuses entirely on bringing the searched related news and summaries to your Android device on one click with real-time update widget provided from the various tweets. The application scraps the data regarding the disasters from the twitter posts and presents the graph accordingly. 

#### Scope:
The whole project idea is implemented in two phases:
1. Provide help to the Humanitarian organizations, governmental and local authorities, and NGOs to pinpoint the area and provide easy location search.
1.1 The app will the scrap Twitter for tweets corresponding to the input provided and a graph showing the number of tweets related to the keyword(in case disaster is given as input). 
1.2 If the number of tweets is above a certain bound, then we can assume that a disaster is going to happen.
1.3 This will help people evacuate as well as inform the authorities of the upcoming disaster. Hence more help could be provided for evacuation.
1.4 It also helps to spread awareness among other citizens using retweets which calculates the area with is more in need of security operations.

1. Help local people in a flood-prone area:
1.1 Due to the loss of an active internet connection, people are not able to send for help.
1.2 Our project helps in providing a network in case of floods. 
1.3 A device called a Node-MCU is used to provide a wifi network. One Node-MCU device gives a range of approximately 40-60 metres. 

#### Definition:
1. CRF: Conditional Random Fields are a class of statistical modelling method which is used for pattern recognition. 
1. Name Entity Recognition: A process where an algorithm takes a string of text,input and identifies relevant nouns (people, places, and organizations) that are mentioned in that string.
1. Word Embedding: Similar words into continuous vector space for word level analysis.

#### Acronyms:
1. NER: Named Entity Recognition 
1. biLSTM: Bidirectional Long Short Term Memory
1. CRF: Conditional Random Field

#### Technical Overview:

```What issue is this app solving?```

Drastic increase in the number of people saved from disasters.
Streamlining the operation of humanitarian operations to increase efficiency.
Analyzing the data and using it to generate reports related to a disaster that could help humanitarian organizations better respond to the varying needs of individuals according to the disaster in an affected area.
Given the volume of data, the manual process may not always be manually practical so we are using graphs for managing the task.
Application is built the resilience of the poor and those in vulnerable situations, and reduce their exposure and vulnerability to climate-related extreme events and other economic, social and environmental shocks and disasters


### Architectural Design:
#### Workflow: 

##### Backend:
We aim to provide rescue operations considering all the possible condition:
###### Internet connection is available
Our methodology uses Twitter as a social sensor is proposed. This is done by extracting information in a sequential way using Named Entity Recognition (NER), which aims to describe entities, such as places, persons, and organizations. It considers the information about each word in a tweet (max of 250 words a post can have) and fetching the keywords to properly identify a place. To achieve this, words are tokenized and transformed into word embeddings to represent them as vector in space by using the NER algorithm. To ensure high classification accuracy in data is achieved extraction techniques, a Recurrent Neural Network variant, i.e., a Bidirectional Long Short-Term Memory (biLSTM) network, is used which considers contextual information in both directions of a word in a tweet, thereby making the data efficient. Sometimes, users can tweet about a calamity after one year of its occurrence(or after a long period of time), then at that time also these tweets can match with the keyword and these tweets will be processed and a graph will be plotted showing that the same calamity is happening even after its occurrence long back which should not happen. To avoid this scenario, after processing the tweets we will compare the location keyword of the tweet with the location keyword of the tweet that is tweeted by the weather forecast team and if it matches we will consider that tweet for plotting the graph and if those tweets does not match(which means that there is no such calamity) then that tweet will not be considered for plotting the graph.
After classifying Tweets with NER tags we get the location of the tweet using which we get the latitude and longitude coordinates by means of Twitter REST API. Finally, a Kernel Density Estimation (KDE) algorithm is used to plot the graph that gives us the view of the intensity of the calamity in disaster prone areas.




###### Technology breakdown occurs and there is no internet connection available 
Then a local network is established by the government using a third-party i.e. node MCU, which have the basic software installed in them and the government drops these devices in the affected places. These node MCU act like a hotspot device for the people stuck in some isolated place and are to be rescued. Once the people get the range and connected to the node MCU they get access to the form that allows the user to input the name, requirements needed etc. Once the user submits the form, the government gets the location in terms of latitude and longitude and aid can be provided to the people stuck.
Once the inputs are received, the government can locate places with the higher people stuck and the more rescue teams can be sent over that place. Also using Dijkstra’s algorithm (helps to find the shortest path according to the conditions provided) we will find the shortest path possible to rescue the refugees.



This is the form that gets generated when the user is in the range of a node MCU


Mapping of all the inputs received from the refugees

Graph is plotted using Dijkstra’s Algorithm



#### Future Extensions of the app:
The app can be extended to provide detailed information regarding the calamity and tells you important information such as the storm’s, earthquake etc. location relative to your location. The application can send alerts and push notification to the user based on the location.
The application platform also provides users to prepare for, respond to and recover from natural disasters.
The application can also track the person and the person in need of emergency can send an SOS request that will help the organization and the government to rescue him.
















































