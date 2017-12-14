### 11. Lấy tổng lượt view của từng category thông qua blog và news
```mysql
SELECT c.title, SUM(b.view + n.view) AS view FROM news AS n JOIN category AS c
  ON n.category_id = c.id JOIN blog AS b
  ON b.category_id = c.id
  GROUP BY c.id;
```