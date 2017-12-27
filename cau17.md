###17. Select 10 blog mới nhất được tạo bởi các user active
```
SELECT b.* 
FROM `train-mysql`.blog as  b inner join `train-mysql`.user as  u
on b.user_id=u.id
WHERE u.is_active=1
ORDER BY b.create_at desc limit 10;
```