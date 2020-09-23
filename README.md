# Final-Project---Spotify
# Which Audio Features Determine A Top 10 Song?

With music streaming services on the rise, and consumers always looking for the hot new song, it is more important than ever for music artists and producers to release a song with the right balance of audio features. Rather than having to spend thousands of dollars to constantly test the market, looking at the data of audio features from hit songs can be very telling.

# Data Cleaning, EDA, Feature Selection, and Feature Engineering

The data used for this project involved web scraping from Spotify,  utilizing the csv files of the Top 200 weekly charts from the Spotify website, as well as using Spotify’s APi to extract the audio ID’s. Aside from having to merge multiple dataframes, the data was relatively clean. I initially looked at the difference of popularity of songs compared to the audio features. I than dove into: 

![Test Image 4](https://github.com/jbillet/Final-Project---Spotify/blob/master/Screen%20Shot%202020-09-23%20at%202.17.40%20AM.png)

![Test Image 4](https://github.com/jbillet/Final-Project---Spotify/blob/master/Screen%20Shot%202020-09-23%20at%202.17.47%20AM.png)

![Test Image 4](https://github.com/jbillet/Final-Project---Spotify/blob/master/Screen%20Shot%202020-09-23%20at%202.17.53%20AM.png)

![Test Image 4](https://github.com/jbillet/Final-Project---Spotify/blob/master/Screen%20Shot%202020-09-23%20at%202.17.59%20AM.png)


As you can see, the liveness of songs, danceability of songs, and loudness of songs all fall under certain parameters to move up in the charts. There is a clear distinction that songs which make the Top 200, and let alone the Top 10 should have their audio features set to that.



# Modeling

I ran multiple models including: K-Best Features, GridSearch Logistic Regression, KNN, Decision Tree, Random Forest, Voting CLassifier, and XG Boost. When evaluating the models by Accuracy, the XG Boost model performed the best with an accuracy score of 96% (Gridsearch Logistic Regression came close at 95%!)

# Conclusion

This is a great start for any music label to start with. I was able to identify certain features which play a role in a songs success. The future is built on data, and with the industry constantly growing, labels and private artists will find looking at features of popular songs more and more valuable. In the future, I would like to build a recommendation system for music labels and artists to use. This will be able to expand their outreach into different music verticals and help them continue to grow their brand, and following.

Presentation Link: https://docs.google.com/presentation/d/1eREDMA-W3fG22I8RHDZpdv9Sm_j8o2e52Z-ebgX80j8/edit#slide=id.g9a659aed1a_0_628
