# Investigating-Netflix-Movies
Exploratory data analysis on Netflix movies from the 1990s to find the most frequent movie duration and count short action movies (&lt;90 mins) from that decade.

markdown
Netflix 1990s Movie Analysis

This project performs **exploratory data analysis (EDA)** on the netflix_data.csv dataset to explore Netflix movies released during the **1990s decade (1990–1999)**.

Objective
- Identify the **most frequent movie duration** (in minutes) for movies from the 1990s.  
  → Saved as an integer variable called ** duration`**.  
- Count how many **Action movies** from the 1990s are **shorter than 90 minutes**.  
  → Saved as an integer variable called ** short_movie_count`**.

Approach

python
# Assuming netflix_df is already defined and contains the necessary data
# We need to filter netflix_df to get the movies and assign it to frequent_movies_df

frequent_movies_df = netflix_df[netflix_df["type"].str.lower() == "movie"]

movies_90s = frequent_movies_df[
    (frequent_movies_df["release_year"] >= 1990) & 
    (frequent_movies_df["release_year"] <= 1999)
]

movies_90s["duration"] = movies_90s["duration"].astype(int)

duration = int(movies_90s["duration"].mode()[0])
print(duration)
print("Most frequent duration:", duration)

short_movie_count = movies_90s[
    (movies_90s["duration"] < 90) &
    (movies_90s["genre"].str.contains("Action", case=False))
].shape[0]
print("Short Action movies count:", short_movie_count)




Output Variables

| Variable            | Description                               | Example Output |
| ------------------- | ----------------------------------------- | -------------- |
| duration         | Most frequent movie duration in the 1990s | e.g. 90     |
| short_movie_count | Count of Action movies under 90 minutes   | e.g. 12      |


Requirements

* Python 3.8+
* Pandas library
  Install using:

  bash
  pip install pandas
  


How to Run

1. Open the Jupyter Notebook (.ipynb) or Python script.
2. Ensure netflix_data.csv is in the same directory.
3. Run all cells — the code will print:

   * The **most frequent duration**
   * The **short action movie count**



Dataset

* **File:** netflix_data.csv
* **Columns used:** type, release_year, duration, genre



 License

MIT License



## 👩‍💻 Author

**Deepika Koppineni**
*Exploratory Data Analysis | Netflix 1990s Movies*



