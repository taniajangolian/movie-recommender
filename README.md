# Movie Recommender

I wanted to see how well a simple "people who liked this also liked that" recommender works on real ratings, and where it breaks down. I built one from scratch using the MovieLens small dataset (about 100,000 ratings from 610 users) and then checked the results by hand.

## What I did
- Dropped movies with fewer than 10 ratings, which left 2,269 movies
- Centered each user's ratings around their own average, so harsh and generous raters are comparable
- Measured movie-to-movie similarity with cosine similarity
- Wrote a function that returns the 10 most similar movies for any title
- Tested a filter that requires more users in common, and measured what it did to quality and coverage

## What I found
It works well for movies with a distinct fan base. Pulp Fiction's top 10 were all crime and drama classics, and The Matrix gave me Fight Club, Memento and Gattaca. It works poorly for broad crowd-pleasers like Titanic, whose picks were scattered across genres. Requiring more users in common cleaned up weak picks, but at 30 users only 24% of movies could still get a full list, so I kept a low cutoff.

## How to run it
1. Clone this repo
2. Install the packages: `pip install pandas numpy scikit-learn matplotlib seaborn requests jupyter`
3. Open `movieanalysis.ipynb` in Jupyter and run all cells (it downloads the data itself)

## Data
[MovieLens](https://grouplens.org/datasets/movielens/) from GroupLens, University of Minnesota. The small dataset was last updated in 2018.