### 10. Lấy Category có tồn tại blog hoặc news đã active (không được lặp lại category)
```mysql
(SELECT DISTINCT c.id, c.title FROM category AS c JOIN blog AS b ON c.id = b.category_id)
UNION
(SELECT id, title FROM news WHERE is_active=1)
```