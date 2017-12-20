###10. Lấy Category có tồn tại blog hoặc news đã active (không được lặp lại category)
```
SELECT distinct(`train-mysql`.category.id),`train-mysql`.category.title,`train-mysql`.category.description
FROM `train-mysql`.category,`train-mysql`.blog,`train-mysql`.news
WHERE `train-mysql`.category.id=`train-mysql`.blog.category_id 
		or (`train-mysql`.category.id=`train-mysql`.news.category_id and `train-mysql`.news.is_active=1);
```