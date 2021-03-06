# Final-Project---Spotify
# Predicting Which Top 200 Song Will Make The Top 10 List

With music streaming services on the rise, and consumers always looking for the hot new song, it is more important than ever for music artists and producers to release a song with the right balance of audio features. Music labels and artists tend to follow trends and have an easier time cracking the top 200 list, but is there data to predict which song will grab a Top 10 spot? We take a look at the features of songs to determine if this is possible. 

# The Road To Determining Which Features Matter When Producing a Song (Roadmap, Data Cleaning, EDA, Features) 

The following will allow you to have a clear understanding how how I obtained the necessary data to complete this project:

- Scraped artist names from the Spotify website. This turned out to be an important role in order to sync artist names to the future top 200 list of songs. 

- I then downloaded the csv files from the Spotify Top 200 Charts dating back to 2016

- After downloading the csv files, I utilized the Spotify API to fetch the audio features of each song (including, but not limited to: tremble, acousticness, liveness, loudness).

## The Roadmap:

First look at the “Spotify Data” Jupyter Notebook on the Master branch of my github account As you can see, during the Webscraping portion of this project, I had to clean up the data to ensure only certain words throughout the features were left (compared to all of the commas and unnecessary jargon)
As you scroll below, you will be able to see the imported Spotify Top 200 song features via csv files. I parsed through those filed extracting artist names, song names, chart positions, and number of streams, and song ID’s. You will then be able to scroll down and see the API call. Initially, I tested the call on one song and realized that it did effectively call each audio feature from the specified song. After doing this test, I used that same for-loop to call the audio feature to over 30,000 songs on Spotify.  Utilizing the Spotify API call I was able to sync the song features with the data obtained via webscraping, along with the Top 200 Song chart. I did this by matching song ID’s to noe another.
 
Taking a look at the “Final Notebook” on the Master branch of my github, you can initially see my imports of all of the necessary csv files to start my EDA process by combing through the data. As expected, there was not much feature engineering that needed to be done due to the fact that the features looked at were called by the API (Tremble, Liveness, Loudness, etc).

## Spotify Index
The following is a list of features and short descriptions to have a better understanding of the data (directly pulled from the SPotify website):
- Time_signature: The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure).
- Acousticness: A confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic.
- Danceability: Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable. 
- Energy: Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy.
- Instrumentalness: Predicts whether a track contains no vocals. “Ooh” and “aah” sounds are treated as instrumental in this context. Rap or spoken word tracks are clearly “vocal”. The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content. Values above 0.5 are intended to represent instrumental tracks, but confidence is higher as the value approaches 1.0. 
- Liveness: Detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live. A value above 0.8 provides strong likelihood that the track is live.
- Loudness: The overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track and are useful for comparing relative loudness of tracks. Loudness is the quality of a sound that is the primary psychological correlate of physical strength (amplitude). Values typical range between -60 and 0 db. 
- Speechiness: Speechiness detects the presence of spoken words in a track. The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value. Values above 0.66 describe tracks that are probably made entirely of spoken words. Values between 0.33 and 0.66 describe tracks that may contain both music and speech, either in sections or layered, including such cases as rap music. Values below 0.33 most likely represent music and other non-speech-like tracks.
- Valence: A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).
- Tempo: The overall estimated tempo of a track in beats per minute (BPM). In musical terminology, tempo is the speed or pace of a given piece and derives directly from the average beat duration.
- ID: The Spotify ID for the track
- URI: The SPotify URI for the track
- Track Name: Song tiel
- Artist: Artist who sings the song
- Chart Position: What position the song was in on the chart ranking
- Week of: Which week the song was in the Top charts

# Visualizations

To visualize what the data describes, I built out multiple visualizations below:

![Alt text](https://github.com/jbillet/Final-Project---Spotify/blob/master/Spotify%20ReadMe%20Pictures/Song%20Feature%20Weighted%20vs%20Popularity.png)

- Song Feature vs weighted popularity: As you can tell by the chart, each feature plays a different role in the popularity of a song. In this instance, when instrumentalness was at 0.0, the popularity rose tremendously. Liveness and Danceability also both rose in popularity when racing in between, respectively, 0.0-0.2.

![Alt text](https://github.com/jbillet/Final-Project---Spotify/blob/master/Spotify%20ReadMe%20Pictures/Danceability%20of%20Songs%20Top%20200:10.png)

- Unsurprising, Danceability for the Top 200 and Top 10 were relatively similar in comparing popularity.
 
![Alt text](https://github.com/jbillet/Final-Project---Spotify/blob/master/Spotify%20ReadMe%20Pictures/Liveness%20of%20Songs%20Top%20200:10.png)
 
- The Liveness of songs had the same range for the best results. Around 0.1 seems to be the sweet spot for the Liveness of the Top 200 and Top 10.
 
![Alt text](https://github.com/jbillet/Final-Project---Spotify/blob/master/Spotify%20ReadMe%20Pictures/Loudness%20of%20Songs%20Top%20200:10.png)
 
- Similar to the Liveness, the Loudness seems to have a sweet spot for popularity in terms of range of Loudness. This seems to be around -5 for both, the Top 200 as well as the Top 10.

# Hypothesis Testing
### Top 10 vs Top 200
- Ho: There is no difference in acousticness in the Top 10 songs of the Top 200 list
- Ha: There is a difference in acousticness in the Top 10 songs of the Top 200 list

![Alt text](https://github.com/jbillet/Final-Project---Spotify/blob/master/Spotify%20ReadMe%20Pictures/Acousticness%20vs%20Time%20on%20Charts.png)

We fail to reject the Null hypothesis. There is no significant significance


# Modeling

In order to predict my goal, I used a Dummy Classifier model as my baseline model to classify a song in which to determine whether it made the Top 10 charts or not. In order to accurately judge my models, I realized that I needed to use the F1 metric. F1 is a metric which is the combination of Precision and Recall. This will tell me if my model is accurately predicting both classes instead of looking at it’s overall accuracy. My baseline model had a 95% accuracy but 0% F1 Score, this indicated to me that my model was struggling with the large class imbalance in my data. Using SMOTE, I created artificial cases to balance my Top 10 to my non-top 10 class. After solving that class imbalance, I ran multiple models including: K-Best Features, Logistic Regression, KNN, Decision Tree, Random Forest, Voting Classifier, and XG Boost. My best model was the Voting Classifier as it had a 38% F1 score and still maintained 88% accuracy.

When determining which features are the most important to making the Top 10 chart, I looked at the coefficients in two models that performed well; Decision Tree and Random Forest. Looking at the top four features, you can see that Random Forest ranked Liveness (0.13856450371489015) , Duration (0.13418215703082687), Energy (0.13145760225385641), and Tempo (0.12911558396700318) as the most important. When taking a look at Decision Tree, you can see that Duration (0.1571872728917043), Liveness (0.15085107527868655), Tempo (0.1380435496673679) and Valence (0.13801515656471408) were the most important in determining a Top 10 song.  
 
# Conclusion

This is a great start for any music label to start with. I was able to identify certain features which play a role in a songs success. The future is built on data, and with the industry constantly growing, labels and private artists will find looking at features of popular songs more and more valuable. In the future, I would like to build a recommendation system for music labels and artists to use. This will be able to expand their outreach into different music verticals and help them continue to grow their brand, and following.

Presentation Link: https://docs.google.com/presentation/d/1eREDMA-W3fG22I8RHDZpdv9Sm_j8o2e52Z-ebgX80j8/edit#slide=id.g9a659aed1a_0_628

Linkedin: https://www.linkedin.com/in/joey-billet-2561848b/
