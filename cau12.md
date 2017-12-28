###12. Lấy blog được tạo bởi user mà user này không có bất kỳ comment ở blog
```mysql
select bl.*
from user as us inner join blog as bl on us.id=bl.user_id
where us.id NOT IN (
select distinct user_id from comment where target_table="blog"
);
```