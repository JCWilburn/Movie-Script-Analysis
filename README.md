# Script-Analysis and Review Prediction

#Problem Statement
A movie script (or screenplay) is often considered the blueprint.  While a movie may not look exactly like this blueprint, it often provides a guideline for the production of a movie.  Additionally, these scripts have been chosen from thousands of submissions.  Based on the script contents, can a movie's success be attributed to its underlying script?

#Data Collection
Started by collecting scripts from Internet Movie Script Data Base (IMSDB).  Captured 1165
Wanted to scrape Independent Movie Database (IMDB) but they no longer have an open API, decided to use The Movie Database (TMDB) API
Used TMDB to scrape based on the titles pulled from IMSDB, then used the TMDB scrape to scrape IMDB
Combined them into one large dataframe and dropped nulls.  


#Exploratory Analysis
When looking at the movie scripts.  A few challenges are apparent.  
1) The most used words in each script tends to be the character names
2) Some scripts contain direction in them (shooting angles, views, etc.)
3) It seems that the scripts that are available are largely movies with favorable reviews

#NLP
Started by CountVectorizing the scripts and playing with the parameters (minimum inclusion, maximum inclusion)
Eliminated any columns that were floats (1, 2,... etc.)

Also used TF-IDF Vectorizorer
Eliminiated any columns that were floats as well

#Modeling
Initially ran models on each
CountVectorizer - Linear Regression, Random Forest Regression
TF-IDF - Linear Regression, Random Forest Regression

#Results
Tried to predict the number of stars (10 star scale) based on the underlying script corpus.  The scores are not "exactly" where I want them to be
With the scores on the training data often hovering close to 1.0 while the testing data scores are large and negative on the Linear models and less than 0.10 on the Random Forrest

#Future Steps 
Want to run these models with n-grams, possibly testing with ridge and lasso
Created new columns based on a critical success measure (Stars of a movie > mean Stars of all the movies)
Created a new column based on larger financial success (Movie's Revenue - Movie's Budget > $20M)

Want to test for these new y variables
