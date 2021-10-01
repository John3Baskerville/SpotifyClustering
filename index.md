[Code](https://github.com/John3Baskerville/SpotifyClustering/blob/main/Juypter%20Notebooks/SpotifyClustering2.ipynb)

Before I started analysis on my personal spotify library, I needed to collect the data from Spotify. Luckily, [spotipy](https://spotipy.readthedocs.io/en/2.18.0/), a lightweight Python library for the Spotify Web API is available. Spotipy allowed me to connect to my personal spotify account and extract whichever personal playlists I needed. I use the [pandas](https://pandas.pydata.org/) python libraries to build tables and read data from JSON elements which helps me easily manipulate the raw data.

Once the data is imported from spotify, I use each song ID to format attributes and song title into a large table with each row representing a song found in my library. I then saved the table into a csv file for late use.

*data table picture*


<img src="http://localhost:8888/view/Desktop/JohnBaskervilleGitRepos/SpotifyClustering/Juypter%20Notebooks/projectImages/violinplots.png?raw=true" alt="violinplot">
