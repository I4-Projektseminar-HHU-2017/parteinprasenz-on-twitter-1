A project by Nils Tecklenborg 

Heinrich-Heine Universität Düsseldorf

Distributed under the GNU General Public Licence v3

Latest Changes 12.08.2017

Knowledge Technology and Twitter 1.0

This Project Knowledge Technology and Twitter consists of two programs. It aims to be a simple solution for collecting tweets from Twitter and gain knowledge by analyzing text and metadata.
The first programm "Twitteranalyse" collects Tweets from any topic of interest and safes them into a SQLite database. 
The second program "Datamining" offers various functions to analyze the collected Tweets, using SQLite statements, the matplotlib for some graphics and WordCloud for some TagClouds.

Twitteranalyse

At first some words to the inspiration for this program. 
This Code is inspired by a Stackoverflow thread and the answer of User Balazs https://stackoverflow.com/questions/37398609/save-data-to-sqlite-from-tweepy


1. Register as a Twitter developer

You need to register as a Twitter developer to get the necessary Access Tokens for the API. This can be done here: http://dev.twitter.com 

The Tokens will be generated after the successful registration. You need to copy and paste them into the Code. 
The connection with the Twitter API is handled by the tweepy library.

Tweepy Documenation: https://github.com/tweepy/tweepy

Twitter API Documenation: https://dev.twitter.com/streaming/reference/post/statuses/filter

2. Connect to the correct database

This project contains several example databases that can be used. Paste the correct path into the sqlite3.connect statement. 
A tutorial how to use SQLite within python can be found here: http://www.python-kurs.eu/sql_python.php.

3. Feel free to modify the CustomStreamListener

The StreamListener handles the incoming tweets. You can modify the behaviour on incoming tweets by changing or adding code to the on_status function.
This Version safes 11 different values from every tweet:

- Tweet ID
- Time Stamp
- User ID
- Text
- Hashtags
- Links
- Mentions
- Language
- Sentiment
- Answer to Tweet ID (If the tweet is an answer to another tweet, the ID of this "original" tweet will be safed here)
- Answer to User ID (If the tweet is an answer to another tweet or user, the ID of this user will be safed here)

Any value, except the Sentiment, is extracted direct from the tweets metadata. The sentiment is generated by the Textblob library (https://textblob.readthedocs.io/en/dev/).
Feel free to change or add values depending on your needs.

4. Choose your keywords of interest

Either insert one of the given keyword lists into the startstream method or create your own. Take care that the database you're connected to in Step 2 matches your theme.


Dataminig

Dataming offers a range of functions that analyze the databases filled by twitteranalyse before.

1. Connect to the correct database

Like in twitteranalyse connect to the database of your interest.

2. The differenct funtions

 - cloud: Creates a Wordcloud where the size of the words depends on the frequency of their occurrence in the text. You can choose whether you want to analyze the text of every tweet or just hashtags. 
 Use the correct stopwordlist for the theme or create your own one. Without stopwordlist there will be a lot of useless words in the wordcloud.

 - language_analyse: Displays the distribution of the language in a pie chart.
 
 - most_answered_tweet: Prints a list of the top 10 most answered tweets by tweets from the database
 
 - most_answered_user: Displays the distribution of the top 10 most answered users by tweets from the database in a pie chart.
 
 - most_common_hashtags: Prints a list of the top 50 most common hashtags 
 
 - most_frequent_user: Prints a list of the top 10 most frequent users in the database
 
 - most_mentioned_user: Displays the distribution of the top 10 most mentioned users by tweets from the database in a pie chart.
 
 - sentiment: Prints the distribution of the sentiments
 
Feel free to add any new funcitons or change any function in a way you like.


If you have any questions about my project please feel free to contact me by email.
contact: nils.tecklenborg@hhu.de
