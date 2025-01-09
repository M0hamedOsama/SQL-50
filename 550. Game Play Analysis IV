WITH login_date AS (SELECT player_id, MIN(event_date) AS first_login
FROM Activity
GROUP BY player_id),

recent_login AS (
SELECT *, DATE_ADD(first_login, INTERVAL 1 DAY) AS next_day
FROM login_date)

SELECT ROUND((SELECT COUNT(DISTINCT(player_id))
FROM Activity
WHERE (player_id, event_date) IN 
(SELECT player_id, next_day FROM recent_login)) / (SELECT COUNT(DISTINCT player_id) FROM Activity), 2) AS fraction
