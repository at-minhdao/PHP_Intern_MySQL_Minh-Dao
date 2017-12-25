### 18. Lấy số lượng Blog active của user có id là 1,2,4
```mysql
SELECT u.full_name, count(u.id) AS number_blog 
FROM blog 
JOIN user
ON blog.user_id = user.id 
WHERE user.id IN(1,2,4) AND blog.is_active = 1
GROUP BY user.id;
```