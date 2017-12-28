###13. Lấy 5 blog mới nhất và số lượng comment cho từng blog
```mysql
select count(c.id) as numCmt,b.id
from comment as c inner join blog as b
on c.target_id = b.id
where c.target_table='blog'
group by b.id
order by b.create_at desc limit 5;
```
