### 7. Xoá tất cả comment của user = 2 trong blog = 5
```mysql
SELECT * FROM comment WHERE target_table='blog' AND target_id=5 AND user_id=2;
```