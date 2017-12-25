### 22. Lấy danh sách user đã comment trong 2 blog mới nhất
```mysql
SELECT * 
FROM user
INNER JOIN (SELECT user_id 
            FROM comment
            INNER JOIN (SELECT id FROM blog
                        ORDER BY id DESC
                        LIMIT 2) AS 2blog
            ON comment.target_id = 2blog.id 
            WHERE comment.target_table = 'blog') AS uid
ON user.id = uid.user_id
```