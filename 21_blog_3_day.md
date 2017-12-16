### 21. Lấy blog được tạo trong 3 ngày gần nhất
```mysql
SELECT date(created_at) AS day_near FROM blog GROUP BY day_near
	ORDER BY created_at DESC 
```