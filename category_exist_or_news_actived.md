###10. Lấy Category có tồn tại blog hoặc news đã active (không được lặp lại category)
```mysql
SELECT distinct(category.id),category.title,category.description
FROM category,blog,news
WHERE category.id=blog.category_id 
		or (category.id=news.category_id and news.is_active=1);
```
