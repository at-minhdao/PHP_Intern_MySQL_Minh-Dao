### 21. Lấy blog được tạo trong 3 ngày gần nhất
```mysql
SELECT * FROM blog WHERE datediff(now(), created_at) < 3;
```