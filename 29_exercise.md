### 29. Lấy số lượng user 1 đang follow
```mysql
SELECT count(to_user_id) FROM follow WHERE from_user_id=1;
```