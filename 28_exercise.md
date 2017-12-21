### 28. Lấy số lượng user đang follow user = 1
```mysql
SELECT count(from_user_id) FROM follow WHERE to_user_id=1;
```