###17. Select 10 blog mới nhất được tạo bởi các user active
```mysql
SELECT b.* 
FROM blog as  b inner join user as  u
on b.user_id=u.id
WHERE u.is_active=1
ORDER BY b.create_at desc limit 10;
```