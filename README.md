# When Was the Golden Era of Video Games?


Video games are big business: the global gaming market is projected to be worth more than $300 billion by 2027 according to Mordor Intelligence. With so much money at stake, the major game publishers are hugely incentivized to create the next big hit. But are games getting better, or has the golden age of video games already passed?

This project analyzes video game critic and user scores, as well as sales data for the top 400 video games released since 1977. Through this analysis, we'll search for a "golden age" of video games by identifying release years that users and critics liked best. Additionally, we'll explore the business side of gaming by examining game sales data.

## Project Goals

1. **Search for a Golden Age**  
   - Identify years with the best user and critic ratings.
   - Compare critic and user scores to identify years where the ratings broadly agreed.

2. **Explore Game Sales Data**  
   - Determine the top ten best-selling games and analyze trends in sales.

## Dataset

The database consists of two tables: `game_sales` and `reviews`, with supplementary pre-computed summary tables for advanced analysis (`users_avg_year_rating` and `critics_avg_year_rating`). Each table has been limited to 400 rows for this project, but the complete dataset (with over 13,000 games) is available on Kaggle.

### `game_sales` Table

| Column      | Definition                   | Data Type |
|-------------|------------------------------|-----------|
| `name`      | Name of the video game       | `varchar` |
| `platform`  | Gaming platform              | `varchar` |
| `publisher` | Game publisher               | `varchar` |
| `developer` | Game developer               | `varchar` |
| `games_sold`| Number of copies sold (millions) | `float` |
| `year`      | Release year                 | `int`     |

### `reviews` Table

| Column        | Definition                             | Data Type |
|---------------|----------------------------------------|-----------|
| `name`        | Name of the video game                | `varchar` |
| `critic_score`| Critic score according to Metacritic  | `float`   |
| `user_score`  | User score according to Metacritic    | `float`   |

### `users_avg_year_rating` Table

| Column           | Definition                            | Data Type |
|------------------|---------------------------------------|-----------|
| `year`           | Release year of the games reviewed   | `int`     |
| `num_games`      | Number of games released that year   | `int`     |
| `avg_user_score` | Average user score for that year     | `float`   |

### `critics_avg_year_rating` Table

| Column           | Definition                            | Data Type |
|------------------|---------------------------------------|-----------|
| `year`           | Release year of the games reviewed   | `int`     |
| `num_games`      | Number of games released that year   | `int`     |
| `avg_critic_score` | Average critic score for that year | `float`   |

## Analysis Tasks

### 1. Best-Selling Games

- **Objective**: Find the ten best-selling games.
- **Output**: A DataFrame named `best_selling_games` containing all columns in the `game_sales` table, sorted by `games_sold` in descending order.

### 2. Top Ten Years by Critic Scores

- **Objective**: Identify the ten years with the highest average critic scores, where at least four games were released (to ensure a reliable sample size).  
- **Output**: A DataFrame named `critics_top_ten_years` with columns:
  - `year`
  - `num_games` (number of games released)
  - `avg_critic_score` (rounded to 2 decimal places)  
  The DataFrame will be ordered by `avg_critic_score` in descending order.

> **Note**: Do not use the `critics_avg_year_rating` table for this query.

### 3. Golden Years of Gaming

- **Objective**: Identify years where critics and users broadly agreed on highly-rated games.  
- **Criteria**: Return years where:
  - `avg_critic_score > 9` **OR** `avg_user_score > 9`.  
- **Output**: A DataFrame named `golden_years` with columns:
  - `year`
  - `num_games`
  - `avg_critic_score`
  - `avg_user_score`
  - `diff` (difference between `avg_critic_score` and `avg_user_score`)  
  The DataFrame will be ordered by `year` in ascending order.

## Tools and Techniques

- **Skills Required**:
  - SQL joins and set operations.
  - Data filtering, grouping, and sorting.
  - Data cleaning and manipulation.
- **Data Source**: The complete dataset is available on [Kaggle](https://www.kaggle.com/).

---

