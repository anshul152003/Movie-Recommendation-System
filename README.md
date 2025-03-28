# Movie Recommendation System (C++)

## Overview
This project implements a collaborative filtering-based movie recommendation system using cosine similarity to predict user ratings and provide personalized recommendations.

## Features
- **Load Ratings**: Reads movie ratings from a CSV file into a 2D matrix.
- **Cosine Similarity**: Computes similarity between users based on their ratings.
- **Predict Ratings**: Estimates ratings for unrated movies for a target user.
- **Top-N Recommendations**: Suggests the top-N movies for a given user.
- **Performance Evaluation**: Uses Root Mean Square Error (RMSE) to assess prediction accuracy.

## File Structure
- `main.cpp`: Contains the main implementation, including all functions and the entry point.
- `data/rating.csv`: Input file containing the user-movie rating matrix.

## Prerequisites
- C++ Compiler: GCC, Clang, or any standard C++ compiler.
- Dataset: A CSV file containing the user-movie rating matrix.

## Input File Format
The input file (`data/rating.csv`) should follow this structure:
- Rows represent users.
- Columns represent movies.
- Cell values represent ratings (0 if unrated).

**Example:**
```
5,4,0,3,1
0,0,4,5,3
3,0,0,2,4
...
```

## How It Works
1. **Load Ratings**: Reads ratings from the CSV file into a 2D vector.
2. **Compute Similarity**: Measures user similarity using cosine similarity.
3. **Predict Ratings**: Estimates ratings for unrated movies using similar users.
4. **Rank Movies**: Sorts predicted ratings to suggest top-N movies.
5. **Performance Evaluation**: Compares predictions with actual ratings to compute RMSE.

## Running the Program
### Compile the Program:
```sh
g++ -o recommender main.cpp
```

### Run the Program:
```sh
./recommender
```

### Output:
- Predicted ratings for the target user.
- List of recommended movies.
- RMSE for model accuracy.

**Example Output:**
```
Predicted ratings for user 0:
Movie 12: 4.75
Movie 24: 4.5
Movie 37: 4.25
...

RMSE: 0.837
```

## Functions Overview
### 1. `loadRatings`
**Description**: Loads ratings from the CSV file into a 2D vector.
- **Parameters**:
  - `filePath`: Path to the CSV file.
  - `ratings`: A 2D vector to store the ratings.

### 2. `computeSimilarity`
**Description**: Calculates cosine similarity between two users.
- **Parameters**:
  - `user1, user2`: Rating vectors for two users.

### 3. `predictRatings`
**Description**: Predicts ratings for unrated movies for a given user.
- **Parameters**:
  - `ratings`: The user-movie rating matrix.
  - `targetUser`: Index of the user for whom to predict ratings.

### 4. `rankMovies`
**Description**: Recommends the top-N movies based on predicted ratings.
- **Parameters**:
  - `predictedRatings`: Predicted ratings vector.
  - `topN`: Number of recommendations.

### 5. `calculateRMSE`
**Description**: Computes RMSE for evaluating prediction accuracy.
- **Parameters**:
  - `ratings`: Actual user-movie rating matrix.
  - `predictions`: Predicted ratings matrix.

## Limitations
- Assumes a dense rating matrix; performance may degrade with sparse data.
- Cold-start problem: Cannot recommend movies for new users or new movies.
- Limited scalability for very large datasets.

