### 18. Lấy số lượng Blog active của user có id là 1,2,4
```mysql
SELECT u.full_name, count(u.id) AS number_blog FROM blog AS b JOIN user AS u
  ON b.user_id = u.id WHERE u.id IN(1,2,4) AND b.is_active=1
  GROUP BY u.id;
```