###15. Update rank user = 2 khi tổng số lượng comment của user > 20
```
SET SQL_SAFE_UPDATES = 0;
update `train-mysql`.user set rank=2
where id in (
select u.id,count(c.id) as num from `train-mysql`.comment as c inner join `train-mysql`.user as u
on c.user_id=u.id
group by u.id
having num > 20
)
```