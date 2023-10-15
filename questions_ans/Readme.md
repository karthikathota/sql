1)Calculate the strike rate of all the players in every match.

```sql
SELECT
  name,
  MATCH,
  (
    CAST(score AS FLOAT) / CAST(no_of_balls AS FLOAT)
  ) * 100 AS strike_rate
FROM
  players_details
ORDER BY
  strike_rate DESC;
```

2. Get the highest score of each player who played in the year 2006

```sql
SELECT
  name,
  MAX(score) AS highest_score
FROM
  Player
WHERE
  strftime('%Y', match_date) = '2006'
GROUP BY
  name
ORDER BY
  highest_score DESC;
```

3)Let's generate a performance report for all the players who played in the year 2006.

```sql
SELECT
  name,
  SUM(score) AS total_score,
  CASE
    WHEN SUM(score) >= 150 THEN 'GOOD'
    WHEN SUM(score) >= 100
    AND SUM(score) < 150 THEN 'AVERAGE'
    ELSE 'BELOW AVERAGE'
  END AS badge
FROM
  player
WHERE
  strftime('%Y', match_date) = '2006'
GROUP BY
  name
ORDER BY
  total_score DESC;
```
