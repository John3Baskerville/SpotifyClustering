[Python Code](https://github.com/John3Baskerville/SpotifyClustering/blob/main/Juypter%20Notebooks/SpotifyClustering2.ipynb)

Before I started analysis on my personal spotify library, I needed to collect the data from Spotify. Luckily, [spotipy](https://spotipy.readthedocs.io/en/2.18.0/), a lightweight Python library for the Spotify Web API is available. Spotipy allowed me to connect to my personal spotify account and extract whichever playlists I needed. I use the [pandas](https://pandas.pydata.org/) python libraries to build tables and read data from JSON elements which helps me easily manipulate the raw data.

Once the data is imported from spotify, I use each song ID to format attributes and song title into a large table with each row representing a song found in my library. I then saved the table into a csv file for late use.

Song Data has ~1600 rows and 19 columns
<img src="https://github.com/John3Baskerville/SpotifyClustering/blob/main/Juypter%20Notebooks/projectImages/csvExample.PNG?raw=true" alt="csv_example">

**Data Cleaning**
...

I used the k-prototype clustering algorithm to help separate playlists using a combination of categorical and numerical data. The typical k-means algorithm, which is good for categorizing large datasets, is not reliable when using categorical data as well as numerical data. The cost function in the k-means algorithm calculates euclidian distance wich can not be used with categorical data.  

**Results**

<img src="https://github.com/John3Baskerville/SpotifyClustering/blob/main/Juypter%20Notebooks/projectImages/violinplots.png?raw=true" alt="violinplot">
