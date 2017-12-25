###Lấy số lượng comment trung bình của tất cả blog.
```
SELECT AVG(number)FROM (SELECT target_id,COUNT(id) as number
FROM `train-mysql`.comment 
WHERE target_table="blog"
GROUP BY target_id) avg_comment;
```