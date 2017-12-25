### 24. Lấy 1 blog và 1 news có số lượng comment nhiều nhất
```mysql
(SELECT id, title, target_table 
  FROM blog
  INNER JOIN
    (SELECT target_id, target_table, count(target_id) AS comment
    FROM comment
    WHERE target_table='blog'
    GROUP BY target_id
    ORDER BY comment DESC
    LIMIT 1) AS most_blog
  ON blog.id = most_blog.target_id)
UNION
(SELECT id, title, target_table 
  FROM news
  INNER JOIN
    (SELECT target_id, target_table, count(target_id) AS comment
    FROM comment
    WHERE target_table='news'
    GROUP BY target_id
    ORDER BY comment DESC
    LIMIT 1) AS most_news
  ON news.id = most_news.target_id)
```
