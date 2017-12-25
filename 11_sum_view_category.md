### 11. Lấy tổng lượt view của từng category thông qua blog và news
```mysql
SELECT category_id, SUM(view) AS totalview 
FROM (SELECT category_id, view FROM blog
      UNION ALL
      SELECT category_id, view FROM news) total
GROUP BY category_id;
```