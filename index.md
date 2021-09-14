[Code](https://github.com/John3Baskerville/SpotifyClustering/blob/main/Juypter%20Notebooks/SpotifyClustering2.ipynb)



First steps in the project involve gathering data and formatting it into an easy to read format easily handled in python (.csv). 
* Connect to spotify and download song library (liked songs). The metadata retrieved includes a unique ID which is assigned to every track.

Here are two of the highest correlated features.

- **energy**: Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has high energy, while a Bach prelude scores low on the scale. Perceptual features contributing to this attribute include dynamic range, perceived loudness, timbre, onset rate, and general entropy.	Float
- **loudness**: The overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track and are useful for comparing relative loudness of tracks. Loudness is the quality of a sound that is the primary psychological correlate of physical strength (amplitude). Values typical range between -60 and 0 db.	Float

<img src="https://github.com/John3Baskerville/SpotifyClustering/blob/main/Juypter%20Notebooks/projectImages/snsHeatmap.png?raw=true" alt="heatmap">
