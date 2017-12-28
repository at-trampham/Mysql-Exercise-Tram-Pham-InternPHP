###11. Lấy tổng lượt view của từng category thông qua blog và news
```mysql
SELECT c.id,c.title,sum(b.view) as view_blog,sum(n.view) as view_news
FROM (category as c inner join blog as b on c.id=b.category_id)
	inner join news as n on c.id=n.category_id
GROUP BY c.id;
```