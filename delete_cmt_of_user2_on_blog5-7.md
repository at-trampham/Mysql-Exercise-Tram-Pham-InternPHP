###7. Xoá tất cả comment của user = 2 trong blog = 5
```
DELETE FROM `train-mysql`.comment WHERE target_table='blog' and target_id=5 and user_id=2;

```
