###12. Lấy blog được tạo bởi user mà user này không có bất kỳ comment ở blog
select bl.*
from `train-mysql`.user as us inner join `train-mysql`.blog as bl on us.id=bl.user_id
where us.id NOT IN (
select distinct(c.user_id) 
from `train-mysql`.comment as c inner join `train-mysql`.blog as b on c.target_id=b.id
where c.target_table="blog"
);