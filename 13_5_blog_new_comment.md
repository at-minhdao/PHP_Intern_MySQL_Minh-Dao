### 13. Lấy 5 blog mới nhất và số lượng comment cho từng blog
```mysql
SELECT b.id, b.title, count(c.id) FROM blog AS b JOIN comment AS c
  ON b.id = c.target_id
  WHERE c.target_table='blog'
  GROUP BY b.id ORDER BY b.id DESC LIMIT 5;
```