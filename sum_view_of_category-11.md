###11. Lấy tổng lượt view của từng category thông qua blog và news
```
SELECT c.id,c.title,sum(b.view) as view_blog,sum(n.view) as view_news
FROM (`train-mysql`.category as c inner join `train-mysql`.blog as b on c.id=b.category_id)
	inner join `train-mysql`.news as n on c.id=n.category_id
GROUP BY c.id;
```