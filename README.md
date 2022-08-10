# Movies-ETL

### Gathering movie data for analysis

## Resources: 
  - Data: 
    - wikipedia-movies.json (movie information webscraped from wikipedia in 2019, webscraping script lost)
    - Kaggle's Movie Dataset  ( https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset?resource=download )  
      - Only used movies_metadata.csv and ratings.csv
  - Software: 
    - Python 3.7.14, Pandas 1.4.2, Numpy 1.21.5, SQLAlchemy 1.4.32 
        - Sometimes Windows PC's need psycopg2-binary to run SQLAlchemy
    - Jupyter notebook (notebook server 6.4.8, Ipython 7.31.1)
    - Postgres 13, pgAdmin 4

# The Data
### Manual Exploring and Cleaning
Data_exploring_and_Cleaning.ipynb is my manual, brute force, exploring and cleaning. I explored the wikipedia movies first, it was very dirty:
   - inconsistant data types: Lists, strings and NaN's for everything
   - lots of missing values
   - lots of keys that could be merged
So Dirty I started cleaning as I was exploring, just to understand what I was looking at. In comparision Kaggle's data is very clean; I had to change a few data types, not hunt through it like with the wikipedia movies.
### Merging the Data  
  - Merging the wikipedia movies and kaggle metadata, Kaggle's columns was more complete anytime there was duplicate columns. I filled any missing values with wikipedia before dropping the lesser columns. 
  - Ratings merges with metadata on a different column than wikipedia movies, their common column is id, or movieId, I think of it as Kaggle_id.
  - there was too many reviews to merge all the data together. A summary of the ratings was taken and added to the "Wiki_movie and Metadata" Combination. How many times a movie was given a specific rating.
### Uploading the Data
- uploaded the "movies with ratings" table and the ratings.csv to my local database. the ratings.csv was just incase future analysis was wanted to enhance the depth of ratings knowledge.
# Automated ETL
The following are the same notebook saved and copied at different times, with the goal of building on the last one for an automated cleaning and uploading process:
  1) ETL_function_test.ipynb         :  Goal: Load the data
  2) ETL_cleaning_wiki_movies.ipynb  :  Goal: Start cleaning with the dirtiest, just cleaning wiki movies
  3) ETL_cleaning_kaggle_data.ipynb  :  Goal: Clean Kaggle's Metadata and ratings then merge with wiki movies
  4) ETL_create_database.ipynb       :  Goal: Upload to Database
  5) The Resources folder is screenshots of the queries I ran in pgAdmin to varify the the data uploaded coreectly with the automated function.
