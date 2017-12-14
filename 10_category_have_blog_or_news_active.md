### 10. Lấy Category có tồn tại blog hoặc news đã active (không được lặp lại category)
```mysql
SELECT DISTINCT n.title, c.title FROM news AS n LEFT JOIN category AS c
  ON n.category_id = c.id JOIN blog AS b
  ON b.category_id = c.id
  WHERE n.is_active=1;
```