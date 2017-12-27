###19. Lấy 5 blog và 5 news của 1 category bất kỳ
```
SET @category_id=(SELECT id FROM `train-mysql`.category ORDER BY RAND() LIMIT 1);
(SELECT category_id,title,view,is_active,content FROM `train-mysql`.blog as b WHERE b.category_id=@category_id limit 5)
UNION ALL
(SELECT category_id,title,view,is_active,content FROM `train-mysql`.news as n WHERE n.category_id=@category_id limit 5)
```