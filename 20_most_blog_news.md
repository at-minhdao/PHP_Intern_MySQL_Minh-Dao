### 20. Lấy blog và news có lượt view nhiều nhất
```mysql
(SELECT id, title FROM blog ORDER BY view DESC LIMIT 1)
UNION
(SELECT id, title FROM news ORDER BY view DESC LIMIT 1)
```