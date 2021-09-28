[Code](https://github.com/John3Baskerville/SpotifyClustering/blob/main/Juypter%20Notebooks/SpotifyClustering2.ipynb)

Before I started analysis on my personal spotify library, I needed to collect the data from Spotify. Luckily, [spotipy](https://spotipy.readthedocs.io/en/2.18.0/), a lightweight Python library for the Spotify Web API was available. Spotipy allowed me to connect to my personal spotify account and extract whichever playlists I needed using python. I use the [pandas](https://pandas.pydata.org/) python libraries to build tables and read data from JSON elements which helps me easily manipulate the raw data.

Once the data is imported from spotify, I format each song ID along with its attributes and title into a large table with each row representing a song found in my library. I extract the table to a csv file for late use.

*data table picture*
<img src="https://github.com/John3Baskerville/SpotifyClustering/blob/main/Juypter%20Notebooks/projectImages/snsHeatmap.png?raw=true" alt="heatmap">
