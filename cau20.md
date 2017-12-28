###20. Lấy blog và news có lượt view nhiều nhất
```
(SELECT id,category_id,title,view,is_active,content FROM `train-mysql`.blog as b ORDER BY b.view desc limit 1)
UNION ALL
(SELECT id,category_id,title,view,is_active,content FROM `train-mysql`.news as n ORDER BY n.view desc limit 1)
```