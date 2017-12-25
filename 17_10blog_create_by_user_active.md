### 17. Select 10 blog mới nhất được tạo bởi các user active
```mysql
SELECT * FROM blog AS b JOIN user AS u
         ON b.user_id = u.id WHERE u.is_active=1
         ORDER BY b.id DESC LIMIT 10;
```