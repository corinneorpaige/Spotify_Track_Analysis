## Dataset from Kaggle:
https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks

## Motivation for Project
I've been looking to work with data from Spotify, and I came across these sets from Kaggle, with artist and track information. I decided to merge them by artist to have more insight into the tracks.
Then, I came up with questions to investigate this Spotify track information:
- By what characteristics can we group/cluster tracks?
- How can we predict the popularity of a track and what are the most important predictors?
- Does the popularity of an artist change if they release a variety of track styles?
- What subcategories of tracks exist?
- For individual artists, what leads to differences in popularity for their tracks?
- Do different genres see varying levels of popularity, and does this change over time?
- How can we visualize the differences between genres of the tracks?

I chose to investigate 3 out of the 6 questions I originally posed:
1. **How can we predict the popularity of a track and what are the most important predictors?**
2. **Do different genres see varying levels of popularity, and does this change over time?**
3. **By what characteristics can we group/cluster tracks? What subcategories of tracks exist?**

## Variables:
### tracks.csv and artists.csv
    
#### Primary:

- id (Id of track generated by Spotify)

#### Numerical:
- **acousticness** (Ranges from 0 to 1)
- **danceability** (Ranges from 0 to 1)
- **energy** (Ranges from 0 to 1)
- **duration_ms** (Integer typically ranging from 200k to 300k)
- **instrumentalness** (Ranges from 0 to 1)
- **valence** (Ranges from 0 to 1)
- **popularity** (Ranges from 0 to 100)
- **tempo** (Float typically ranging from 50 to 150)
- **liveness** (Ranges from 0 to 1)
- **loudness** (Float typically ranging from -60 to 0)
- **speechiness** (Ranges from 0 to 1)

#### Dummy:
- mode (0 = Minor, 1 = Major)
- explicit (0 = No explicit content, 1 = Explicit content)

#### Categorical:
- key (All keys on octave encoded as values ranging from 0 to 11, starting on C as 0, C# as 1 and so on…)
- timesignature (The predicted time signature, most typically 4)
- artists (List of artists mentioned)
- artists (Ids of mentioned artists)
- release_date (Date of release mostly in yyyy-mm-dd format, however precision of date may vary)
- name (Name of the song)

## Instructions:
1. Download tracks.csv and artists.csv from the above Kaggle link and FinalProjectCode.ipynb from this repository.
2. Open FinalProjectCode.ipynb and adjust the file paths for your system, ensuring that tracks.csv and artists.csv will load and all appropriate libraries are installed
3. Run FinalProjectCode.ipynb

## Known Errors:

Mistake in generating factor levels from 'Key' variable

## Resources Used:

Merge: https://towardsdatascience.com/why-and-how-to-use-merge-with-pandas-in-python-548600f7e738

Error: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy

Renaming Columns: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.rename.html?highlight=rename#pandas.DataFrame.rename

Dropping Columns: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.drop.html

LASSO Documentation: https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Lasso.html#sklearn.linear_model.Lasso

String Shortening:Lhttps://www.kite.com/python/answers/how-to-remove-everything-after-a-character-in-a-string-in-python

Fct_lump for Python: https://stackoverflow.com/questions/62996246/equivalent-of-fct-lump-in-pandas

Geom_bar: https://plotnine.readthedocs.io/en/stable/generated/plotnine.geoms.geom_bar.html?highlight=geom_bar

Random DF Sampling: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.sample.html

Spotify API: https://developer.spotify.com/documentation/web-api/reference/#objects-index

