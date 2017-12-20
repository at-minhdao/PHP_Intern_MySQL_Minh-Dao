### 10. Lấy Category có tồn tại blog hoặc news đã active (không được lặp lại category)
```mysql
SELECT DISTINCT c.id, c.title FROM category AS c 
  INNER JOIN blog AS b ON c.id = b.category_id
  LEFT JOIN news AS n ON c.id = n.category_id 
  WHERE b.is_active > 0 OR n.is_active > 0
```