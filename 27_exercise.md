### 27. Blog của user đang được user có id = 1 follow
```mysql
SELECT * FROM blog WHERE user_id IN (SELECT to_user_id FROM follow WHERE from_user_id=1)
```