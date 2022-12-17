# Spotify: Relationship Between Danceability of a Song and Number of Weeks on Chart
<b> Group members: </b> Prae Kongchan, Ninh Nguyen, Jacqueline Guerra, Huiling Xiao, Van Le & Joyce Xinyi Jiang
<br> 
<b> Details: </b> Final Group Project / DSO 510 / Business Analytics / University of Southern California (USC) / Marshall School of Business / M.S. Business Analytics
<br>
<b> Spotify's Data Definitions: </b> Definition of individual track elements, structure and content follows the description provided by Spotify. 
<a href="https://developer.spotify.com/documentation/web-api/reference/#/operations/get-audio-analysis"> (link) </a>
</br>
<b> Documents included: </b>
<ol>
  <li> Spotify Dataset (Cleaned) </li>
  <li> Spotify Model (R) </li>
  <li> Spotify Dataset & Model Visualization (Python) </li>
  <li> Spotify Relationship Analysis PPTX </li>
  <li> Spotify Relationship Analysis Summary Findings </li>
</ol>


# Introduction
What is the similarity between “The Next Episode” by Dr Dre and “Every Breath You Take” by The Police? Both songs have a danceability score of 0.8/1 and above. According to Spotify, danceability is defined as “how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity.” With the rise of TikTok, the danceability of a song became more evident when it is featured in a myriad of short videos, often associated with trends or dance challenges. For example, HUMBLE. by Kendrick Lamar, has a danceability score of 0.9/1 and is featured 761,000 times on TikTok videos; with a peak rank of 1 on Spotify and stayed on the charts for 96 weeks. Parallely, we question whether the danceability of the song contributes to its popularity, which in turn impacts the length of time the song stays on the chart. Hence, we seek to answer the question, “Is there a relationship between danceability and the length of time a song spends on chart?”.

# Approach
What makes a song successful on the charts is difficult to predict. Music is collective, and often listened to in a social context, so individual taste will not always align with the most popular songs of the moment. Additionally, there are many well documented outliers to songs that top the charts; one hit wonders often take the music industry by surprise. In this way, data can help. By assessing each song at a more granular level by musicality, we can assess if there is something specific to each song that enables its popularity. We predict danceability influences the length of time a song stays on the charts because a danceable song is often listened to in a social context: on TikTok, on the radio, in clubs and bars. However, there are many other outcomes that could come from the data. The best predictor for songs staying on the charts the longest could simply be if the song is from a popular artist that has previously had top charting songs. Another option is that social media sites, namely TikTok, are informing the charts themselves, and the songs that are staying on the charts the longest are the songs that TikTok made popular first. Additionally, seasonality could also play an important role in which songs are popular at each time of the year. A data driven approach will allow us to take many variables into account and assess which ones are actually driving song popularity.

# Ideal Experiment
We will use between-subjects (independent measures) design where songs are randomly assigned a level of danceability (none, low, or high), follow that level of danceability throughout the experiment, and observe how it will impact the weeks a song spends on chart. In reality, this experiment is difficult to conduct as a song often consists of multiple attributes which are intertwined.

# Data Exploration & Preparation
To inform our analysis, we have obtained two datasets from Kaggle, sourced from Spotify and one from Github, sourced from TikTok. The first dataset contains information about global top charted songs from 2022 with various attributes given to each song. The following dataset with information about Spotify artists and details such as numbers of streams, etc, which provides an overview to how popular each artist is; as popularity of an artist may potentially affect how long a song stays on the chart. Finally, to further explore how tiktok trends may affect popularity of a song, the last dataset includes information of songs which appeared on TikTok.
<br>
Thus, we have merged the datasets by using artist names and song names as the identifiers. To prepare the data, we first created a dummy variable for TikTok. If there is a match of a track’s name between datasets, it will return 1 for a song that appears on TikTok; 0 otherwise. We removed extreme outliers (values above 95th percentile and 5th percentile) and transformed the data which are right-skewed by logging the variables. The final dataset has 447 rows in total and contains columns like artist name, number of streams, track name, log(number of weeks on chart), log(danceability), log(energy), appearance on TikTok, etc. Additionally, each row represents individual songs with unique attributes. However, songs from the same artist will share the same artist details. Finally, the outcome variable of interest for this analysis would be the log of number of weeks on the chart. </br>

# Descriptive Analytics 
Through data exploration, we have found that there are extreme outliers in our dataset that may potentially impact the outcome and interpretation of our findings. For example, the maximum value for Streams and Weeks On Chart is significantly far from the mean. Hence, they validated our decision of removing outliers and transforming the data to better prepare our model. Moreover, it is evident that it is impossible to have 0 danceability in a song as the minimum value is 0.398. This emphasizes the fact that our ideal experiment with random assignment of danceability is unrealistic as music is always comprised of a multitude of musical elements which gives its individual uniqueness. 

# Model Explanation
We included all variables in our preliminary model; however, we found that Loudness and Energy were highly correlated at 0.713 after assessing the model results. Given that this is significantly higher than the correlation between Log Weeks on Chart and Log Danceability (0.017), we removed Energy to avoid potential issues with collinearity since it was the less significant variable. Once Energy was removed, Loudness became slightly more significant, and the R-squared value remained the same as 0.16, indicating the strength of the model had not changed.

# Conclusion
In conclusion, our control variables, TikTok, Streams and Loudness are observed to be a stronger predictor than our main variable in terms of how long a song may spend on the charts. One reason that danceability could have not been a significant variable is because we assumed more danceable songs would be the ones that are popular on TikTok due to dance trends: however, after assessing the data, we found the assumption to be less linear and there are also a variety of elements that inform TikTok trends. Given the R2 of our model was fairly low at 0.16, it is also evident that outside elements, which we have not included, also plays a role in influencing the results. The elements, for example: 
<br>
<li> Seasonality, in particular Christmas songs topping the charts around the holidays </li>
<li> Movies and TV: often times songs that are trending on TikTok come from Movie and TV soundtracks </li>
<li> Radio Play: how often a song is played on the radio </li>
<li> Artist News: big events in an artist's life can make their songs popular again, namely when an artist dies </li>
</br>
Overall, while, danceability is not a primary factor in music popularity, music popularity is tough to predict in general. Individual music taste is greatly informed by those around you as it’s often listened to in a social context. There are many breakout hits and unexpected comebacks, and most importantly, the joy of music is often vested within its unpredictabilty. 

