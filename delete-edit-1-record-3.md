##3. Xoá và sửa1 dòng dữ liệu trong bất kỳ table nào
#Sửa dòng sữ liệu trong table user
```
UPDATE `train-mysql`.user set full_name='Pham Thi Mai Tram' where id=15;
```
#Xóa dòng dữ liệu trong table user
```
DELETE FROM `train-mysql`.user WHERE id=15;
```