### 13. Lấy 5 blog mới nhất và số lượng comment cho từng blog
```mysql
SELECT blog.id, blog.title, COUNT(comment.id)
FROM blog
LEFT JOIN comment
ON blog.id = comment.target_id
WHERE comment.target_table = 'blog'
GROUP BY blog.id
ORDER BY blog.id DESC
LIMIT 5;
```
