# Spotify-SQL-Data-Analysis
SQL-based analysis of Spotify dataset using PostgreSQL to extract insights on tracks, artists, and albums. Includes exploratory analysis and advanced queries to evaluate streaming performance and user engagement.

---

# Spotify Data Analysis using PostgreSQL

![Alt text](https://github.com/PRATHAMPBHANDARY/Spotify-SQL-Data-Analysis/blob/75d7d69f5f657f2ce52dd1864d220d6238deb08a/SPOTIFY%20LOGO.png)

## Overview

This project involves analyzing a Spotify dataset using PostgreSQL to extract meaningful insights about tracks, albums, and artists.

It covers an end-to-end workflow including data structuring, query development, and performance-focused analysis. The project demonstrates SQL proficiency through queries of varying complexity, from basic to advanced levels.

---

## Technology Stack

* **Database**: PostgreSQL
* **SQL Queries**: DDL, DML, Aggregations, Joins, Subqueries, Window Functions
* **Tools**: pgAdmin 4 (or any SQL editor), PostgreSQL

---

## Project Objectives

* Analyze track, album, and artist performance
* Evaluate engagement metrics such as streams, views, and likes
* Compare streaming trends across platforms
* Apply structured SQL techniques to solve analytical problems

---

## Key Analysis

### Basic Queries

* Retrieve tracks with more than 1 billion streams
* List albums and their respective artists
* Calculate total comments for licensed tracks
* Identify tracks from specific album types
* Count total tracks by each artist

### Intermediate Queries

* Calculate average danceability per album
* Identify top tracks based on energy
* Analyze likes for official video tracks
* Calculate total views across albums
* Compare streaming performance across platforms

### Advanced Queries

* Rank top tracks per artist using window functions
```sql
with ranking_table as
  (select 
     artist,track,
      sum(views) total_views,
      dense_rank() over (partition by artist order by sum(views)  desc ) as rank
  from spotify
  group by  artist,track
  order by artist,total_views desc
)
select * from
ranking_table
where rank <= 3;
```


* Identify tracks with above-average liveness
* Analyze energy variation across albums using CTEs
```sql
WITH CTE_TABLE AS 
  (SELECT
    ALBUM,
    MAX(ENERGY) AS HIGHEST_ENERGY,
    MIN(ENERGY) AS LOWEST_ENERGY
FROM SPOTIFY
GROUP BY 1)

SELECT 
  ALBUM,
HIGHEST_ENERGY - LOWEST_ENERGY AS DIFFRENCE_RATE
FROM CTE_TABLE 
ORDER BY ALBUM DESC;
```
  
* Evaluate energy-to-liveness ratio
* Calculate cumulative likes using window functions

---

## How to Run the Project

1. Install PostgreSQL and pgAdmin (if not already installed)
2. Create the database and tables using the provided SQL script
3. Insert the dataset into the tables
4. Execute the SQL queries step by step
5. Analyze outputs and explore query optimization techniques

---

## Project Structure

```id="3v5qjp"
Spotify-SQL-Analysis/
│── FINAL SPOTIFY PROJECT.sql
│── README.md
```

---

## Next Steps

* **Data Visualization**: Build dashboards using Power BI or Tableau
* **Dataset Expansion**: Add more data for deeper analysis
* **Query Optimization**: Improve performance for large-scale datasets
* **End-to-End Project**: Integrate SQL with visualization tools

---

## Contributing

Contributions are welcome. You can fork the repository, create a new branch, and submit a pull request. You may also raise issues for improvements or suggestions.

---

## License

This project is licensed under the MIT License.

---

## Author

**Pratham P Bhandary**
**Email:** prathamkoni36@gamial.com
**Linkedin:** https://www.linkedin.com/in/pratham-p-bhandary/
---

## Notes

**All SQL queries used in this project are included in the Repository**

