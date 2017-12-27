###18. Lấy số lượng Blog active của user có id là 1,2,4
```
SELECT b.user_id,count(b.id) as numblog
FROM `train-mysql`.blog as  b
WHERE b.is_active=1 AND b.user_id IN (1,2,4)
GROUP BY b.user_id;

```