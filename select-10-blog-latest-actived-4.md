###4. Select 10 blog mới nhất đã active
```
SELECT * FROM `train-mysql`.blog
WHERE is_active=1 
ORDER BY id desc limit 10;

```