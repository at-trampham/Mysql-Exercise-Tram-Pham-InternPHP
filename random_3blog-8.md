###8. Lấy 3 blog bất kỳ (random)
```
SELECT *
FROM `train-mysql`.blog
ORDER BY RAND()
LIMIT 3;
```