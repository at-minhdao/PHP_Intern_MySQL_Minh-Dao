
```mysql
(SELECT id, category_id, title, target_table FROM blog 
    INNER JOIN 
  (SELECT target_id, target_table FROM comment 
  WHERE target_table='blog' AND user_id=1 
  GROUP BY target_id ORDER BY target_id DESC LIMIT 2) AS 2_blog
  ON id = target_id)
UNION
(SELECT id, category_id, title, target_table FROM news 
    INNER JOIN 
  (SELECT target_id, target_table FROM comment 
  WHERE target_table='news' AND user_id=1 
  GROUP BY target_id ORDER BY target_id DESC LIMIT 2) AS 2_blog
  ON id = target_id)
```